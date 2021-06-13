# Stromerrepair
Reverse-Engineeren des ersten Stromers um Motorschäden via DIY-lösung zu beheben

## Absicht:

Entwickeln einer Lösung zur Behebung der "Motorschäden" bei Stromer ST1 Pedelecs.

Diese Motorschäden sind meist Probleme des Controllers (Überhitzung und dadurch Schäden an der im Motorgehäuse verbauten Elektronik oder den Sensoren). Entwickelt werden soll eine Steuerung und Software, welche den bestehenden Controller ersetzt und so das Rad erneut auf die Strasse bringt.

## Konzept:

Als IC soll ein Arduino (oder Atmel-Chip) zum Einsatz kommen. Dieser soll:

1. Mit dem Originaldisplay kommunizieren
2. Den bestehenden Drehmomentsensor auslesen
3. Die Akkuspannung messen und überwachen
4. Einen Brushless ESC ansteuern

## Brainstorming

- Der ESC (Electronic Speed Controller) muss vermutlich etwas überdimensioniert werden, damit er nicht in Rauch aufgeht. Sinnvoll wäre wohl etwas um die 1500W, auch wenn keine so hohen Energiespitzen erreicht werden.
- Da die Akkus keine Kommunikationsschnittstelle haben, geht das mit den originalen Akkus relativ einfach.
- Dort liegen normalerweise einfach die 36v (bzw. irgendwas zw. 33v und 42v je nach Ladezustand) an den Polepins an.
- Der Originale ESC soll aus dem Motorgehäuse ausgebaut werden, die Kabel von den Wicklungen sowie anschlüsse der Hall-Sensoren neu verkabelt und durch die Nabe rausgezogen werden. Der Controller sollte so klein gebaut sein, dass er im Rahmen unterbringbar ist. So wird auch dem Überhitzungsproblem der Elektronik im Motorengehäuse entgegnet.

## Mögliche Hardware:

### Motor-Controller:
- https://vesc-project.com
  - (Programmierbare VESC Controller! Sehr cool!)
- https://makerx-tech.com/collections/x-esc/products/x-vesc4
- https://www.aliexpress.com/item/4000438827676.html
  - 50A controller (max 13s... bei 10s 1800w Dauerleistung 3600w peak; ca. 60$ shipped)

## Dev-Board / IC:

Fraglich ob mit kleinem gestartet und Code nachher auf grösseres Board umgezogen werden kann, wenn mehr Recourcen nötig wären?!
- Rhino Mini 328PB (Atmel 328PB, 2xUART, ca. 5$)
- Pololu A-Star 328PB Micro (Atmel 328PB, 2xUART, ca. 5$)
- ATxmega (z.B. MT-DB-X5, 2xUART, ca 22$)
- Teensy 3.2 (72mhz cortex, 3xUART, ca. 20$)
- ESP8266 (https://de.wikipedia.org/wiki/ESP8266, WLAN, 3$)
- ESP32 (https://de.wikipedia.org/wiki/ESP32, WLAN, BT, 5$)

## Diskussionsforum:

Stromerforum: https://stromerforum.ch/showthread.php?tid=2967

# Hardware des Stromers

## Motor

## Torque Sensor
Der Torque Sensor ist von der Firma IDBike und im Schaltauge integriert.

http://www.idbike.com/sensors

### Specifications TMM Sensor Unit

```Supply voltage: 	5 V
Output voltage: 	0,1 V- 4,9 V
Measuring range sensor unit: 	120 Nm ( High sensitivity) / 300 Nm  (medium sensitivity)
Sensitivity TMM sensor unit: 	 40 Nm/V (High sensitivity)/ 100 Nm/V  (medium sensitivity)
Tolerance on sensitivity: 	< 3 %
Allowable range ZTV (zero torque value): 	  0,5-2 V 
Temperature influence: 	< 1 mV/ ºC
Electrical disturbance: 	< 10 mV
Effect of moisture: 	< 10 mV
Operational temperature: 	-10 - 60 ºC
Storage temperature: 	-40 - 85 ºC
Durability: 	At least 10 million cycles
Protection Class: 	IP66 >> protection aigainst water and dust
```

Auf eine Anfrage an IDBike ob es denn aftermarket Controller mit Support ihres Sensors gäbe, kam folgende Antwort:

"You might take a look at the company Flipsky, who sell VESC controllers online.

I think this controller will work with the Stromer motor also.

We’re developing SW for this controller to accommodate our sensor, this will take a year probably."

### Controller welche den Torque Sensor unterstützen

Es wird des öfterenen erwähnt das der Phasrunner/Baserunner Controller der Fa. Grin Technolgies den Stromermotor unterstützt, ob man auch den Torque Sensor zum laufen kriegt ist noch unklar.

https://ebikes.ca/shop/electric-bicycle-parts/controllers.html
