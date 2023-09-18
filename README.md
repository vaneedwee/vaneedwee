
//Sensor ultrasonico
int trig = 3;
int echo = 2;

int time;
int distancia;

//bomba
int bomba = 5;

void setup() {
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);

  Serial.begin(9600);
  
  pinMode(bomba, OUTPUT);
  analogWrite(bomba, 0);
}

void loop() {
  digitalWrite(trig, HIGH);
  delay(1);
  digitalWrite(trig, LOW);
  
  time = pulseIn(echo, HIGH);
  distancia = time/58.2;

  Serial.print("Distancia del vaso: ");
  Serial.println(distancia);

  if (distancia <= 5){
    //Activacion de bomba
    analogWrite(bomba, 225);
    Serial.println("bomba activa");
       delay(500);
    analogWrite(bomba, 0);
  }
  else {
    analogWrite(bomba, 0);
    Serial.println("bomba inactiva");
  }
}
