# AC-Refrigerant-leakage-detection-and-alerting-system-using-arduino
The main aim of this project is to alert the inmates who are using the AC room during the
night time when there is a leakage of freon and other harmful gases rarely from compressor.
This leakage is really dangerous as it could cause suffocation leading to death of individuals. 
Freon is a tasteless and odourless gas which is commonly used in AC for the purpose of cooling.
This is done with the help of components like tgs 832 A00 (a cfc sensor),an arduino and a buzzer.
code :
int redLed = 12;
int greenLed = 11;
int buzzer = 10;
int smokeA0 = A5;
// Your threshold value
int sensorThres = 100;

void setup() {
  pinMode(redLed, OUTPUT);
  pinMode(greenLed, OUTPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(smokeA0, INPUT);
  Serial.begin(9600);
}

void loop() {
  int analogSensor = analogRead(smokeA0);

  Serial.print("Pin A0: ");
  Serial.println(analogSensor);
  // Checks if it has reached the threshold value
  if (analogSensor > sensorThres)
  {
    digitalWrite(redLed, HIGH);
    digitalWrite(greenLed, LOW);
    tone(buzzer, 1000, 200);
  }
  else
  {
    digitalWrite(redLed, LOW);
    digitalWrite(greenLed, HIGH);
    noTone(buzzer);
  }
  delay(100);
}
