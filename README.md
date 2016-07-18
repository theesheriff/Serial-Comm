# Serial-Comm
//Lacked a push button; so tried to put  together a program that would allow me to switch LED on/off via serial commands from my PC

int ledPin=9;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  
  pinMode(ledPin, OUTPUT);

}

void loop() {
  // put your main code here, to run repeatedly:
  int state;  //state of the LED;on/off
  Serial.write(1||0); //write 1 for on and 0 for off to the arduino
  if (Serial.available()) //check for signal communication
  { 
    state=Serial.read();  
  }
  if (state==1)
  {
    digitalWrite(ledPin, HIGH);
    Serial.println("LED ON");
  }
  else if (state==0);
  {
    digitalWrite(ledPin, LOW);
    Serial.println("LED OFF");
  }
}
