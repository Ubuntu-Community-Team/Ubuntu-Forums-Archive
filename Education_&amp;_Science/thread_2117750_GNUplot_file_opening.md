---
title: "GNUplot file opening"
date: 2013-02-19
forum: Education &amp; Science
---

### Post by huggies15 on 2013-02-19
Hi!

Having problems finding info on how to use gnuplot.

I understand the code "plot filename parameters" will load the code from the file 'filename' and do the parameters set.

What I have is a program that will create a series of files with the filename: temperaturedataTIMESTAMP.log, where the timestamp will constantly change.

What I want if for the gnuplot code to load the newest file, ie, the most recent TIMESTAMP, and run for that.

The idea is that the program will create the data for measuring temp changes, and the gnuplot will print a graph of the results. 

However, need sequential file names as need to keep all the data. Therefore will need to open different files, and 'print' out files with the same name but .png not .log...

ie input temp12_12_12.log output temp12_12_12.png
(next file)
input temp12_13_12.log output temp12_13_12.png etc.

hope that makes sense!

Any help greatly appriciated,
Steve

---

### Post by huggies15 on 2013-02-19
OK, new idea, probably simpler to achieve.
I will save the data file twice, once as gnu.log, and once as tempTIMESTAMP.log.
I will then get gnuplot to open the file gnu.log and process that data (it should be over wirtten by new data when that is acquired).

So how do i get the output to change so it is tempTIMSTAMP.png not just temp.png (where timestamp is the current time/date)

Cheers,
Steve

---

### Post by steeldriver on 2013-02-19
Well the more recent versions of gnuplot have *some* built in loop functionality - although I *think* that so far it only allows iterating through a string list or a sequence of integers

I don't know if it's the right way to do it, but you could generate the filename in the shell, and then call gnuplot non-interactively, effectively constructing the input file on the fly with the data file and output file names getting expanded by the shell e.g.

```
$ plotfile="plotfile"
$ gnuplot <<EOF
set term png                                                                   
set output "$plotfile.png"
plot "$plotfile" using 3:2 with points, "" using 3:2:1 with labels offset -1,-1
EOF

```

---

### Post by huggies15 on 2013-02-19
Hi,
Can you see if my work around makes sense.
I've added a line at the end of my data script to take the output file gnu.png, and copy it to a file named (i hope) gnuTIMESTAMP.png. Therefore the file gnu.png can be over written when the program is next run as there is a copy saved with a different name.

Python code:
```
# Copyright (c) 2012 Matthew Kirk
# Licensed under MIT License, see 
# http://www.cl.cam.ac.uk/freshers/raspberrypi/tutorials/temperature/LICENSE

import RPi.GPIO as GPIO
import time

LED1_GPIO_PIN = 18
LED2_GPIO_PIN = 25
BUTTON_GPIO_PIN = 17
GPIO.setmode(GPIO.BCM)
GPIO.setup(BUTTON_GPIO_PIN, GPIO.IN)
GPIO.setup(LED1_GPIO_PIN, GPIO.OUT)
GPIO.setup(LED2_GPIO_PIN, GPIO.OUT)

GPIO.output(LED1_GPIO_PIN, GPIO.HIGH)

while True:
	if GPIO.input(BUTTON_GPIO_PIN):
		break

while GPIO.input(BUTTON_GPIO_PIN):
	pass

GPIO.output(LED1_GPIO_PIN, GPIO.LOW)
GPIO.output(LED2_GPIO_PIN, GPIO.HIGH)

timestamp = time.strftime("%Y-%m-%d-%H-%M-%S")
prog_start = time.time()
filename = "".join(["temperaturedata", timestamp, ".log"])
image = "".join(["graph", timestamp, ".png"])
datafile = open(filename, "w", 1)
gnu = open("gnu.log", "w", 1)

measurement_wait = 15
button_pressed = False
while True:
	time_1 = time.time()
	tfile = open("/sys/bus/w1/devices/10-000802824e58/w1_slave")
	text = tfile.read()
	tfile.close()
	temperature_data = text.split()[-1]
	temperature = float(temperature_data[2:])
	temperature = temperature / 1000
	datafile.write(str(time.time()-prog_start) + "\t" + str(temperature) + "\n")
	gnu.write(str(time.time()-prog_start) + "\t" + str(temperature) + "\n")
	time_2 = time.time()
	if (time_2 - time_1) < measurement_wait:
		no_of_sleeps = int(round((measurement_wait - (time_2 - time_1)) / 0.1))
		for i in range(no_of_sleeps):
			time.sleep(0.1)
			if GPIO.input(BUTTON_GPIO_PIN):
				button_pressed = True
				break
	if button_pressed:
		break
			

datafile.close()
gnu.close()

import os
os.system("gnuplot temp.plt")

import shutil
shutil.copy(gnu.png, image)

GPIO.output(LED2_GPIO_PIN, GPIO.LOW)
```

GNU code:
```
set terminal png small size 900, 968 transparent# x000000
set output "gnu.png"
set time
set y2tics
set timestamp "%a %b %Y %H:%M:%S" bottom
set title "Temperature Profile" # 0.000000,0.000000  "";
set ylabel "Degrees Centigrade" # 0.000000,0.000000  ""
set xlabel "Time (seconds)"
set key below
plot 'gnu.log' using 1:2 with linespoints,\
set output
```

Any feedback (as in: yes that looks right, or, are you a retard?!) would be good!

Steve

---

