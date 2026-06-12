---
title: "PS3 Controller calibration won't work in Lucid"
date: 2010-06-14
forum: Gaming &amp; Leisure
---

### Post by 4rk3typ3 on 2010-06-14
I'm currently using jscal in lucid and I can't get past calibrating because when it goes to calibrate the joysticks I get a Bus Error. This is using the 64-bit version of lucid, in the 32-bit version I had a segmentation fault. 

jscal -c /dev/input/js0 output

```

Joystick has 28 axes and 112 buttons.
Correction for axis 0 is none (raw), precision is 0.
Correction for axis 1 is none (raw), precision is 0.
Correction for axis 2 is none (raw), precision is 0.
Correction for axis 3 is none (raw), precision is 0.
Correction for axis 4 is none (raw), precision is 0.
Correction for axis 5 is none (raw), precision is 0.
Correction for axis 6 is none (raw), precision is 0.
Correction for axis 7 is none (raw), precision is 0.
Correction for axis 8 is none (raw), precision is 0.
Correction for axis 9 is none (raw), precision is 0.
Correction for axis 10 is none (raw), precision is 0.
Correction for axis 11 is none (raw), precision is 0.
Correction for axis 12 is none (raw), precision is 0.
Correction for axis 13 is none (raw), precision is 0.
Correction for axis 14 is none (raw), precision is 0.
Correction for axis 15 is none (raw), precision is 0.
Correction for axis 16 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 17 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 18 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 19 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 20 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 21 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 22 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 23 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 24 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 25 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 26 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 27 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751

Calibrating precision: wait and don't touch the joystick.
Bus error

```

jscal output to file
```

jscal -s 28,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751 /dev/input/js0

```


I was able to get jscalibrator to work in lucid but it apparently has a bug and causes the analog sticks to become unresponsive. Without calibrating the joystick it acts like I am constantly moving the analog sticks because they have no null zone specified. jstest yields that the joysticks are, in fact, moving on a very small scale (spazzing 1 unit in any direction)

I've come across information on how to specify a nullzone but his directions were incredibly vague ([http://ubuntuforums.org/showthread.php?t=1175430&page=2]("http://ubuntuforums.org/showthread.php?t=1175430&page=2"))
If someone could give me information on how to specify a nullzone on the jscal output file or a better program I can use (I've used jscal, jscalibrator, and sixad so far) I'd really appreciate it.

---

### Post by 4rk3typ3 on 2010-06-14
UPDATE: I may have figured out a solution to the null zone problem, however, when I run jscal -s to set my new adjustments, I get an error that the number of axes doesn't match. Command line has 28 and my file has 28 but jscal -s is reading 16 from my file...

Method to recreate:

Printed output of jscal to a "calibration file"
```
jscal -p /dev/input/js0 > joystick.cal
```
Modify joystick.cal to look like this:
```
jscal -s 28,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745,1,0,112,142,5534757,5534745 /dev/input/js0
```

Used file to run calibration command (same as above)
```
source joystick.cal
```

Error: 
```
jscal: joystick has different number of axes (16) than specified in command line (28)
```

---

### Post by 4rk3typ3 on 2010-06-15
UPDATE:
So I was able to acquire the source code and discovered that the original creator had limited the max number of axes to 16, a quick modification and a make later, I had a working jscal that allowed me to configure 28 axes. I was also able to discover that by adding the information that was at the end of my file to the beginning, I gained the control over the Axes that I needed. It is still not quite 100% yet and it doesn't seem to want to work properly in applications but jstest shows that the calibrations are working just as they should at the moment. Still working this issue and any help would be fantastic. 

At the rate this is going, this may become a how to :D

---

### Post by sepius on 2010-06-15
Your number set looks a bit different to my number set, am I right in seeing you have 28 axis?, not sure if the calibration worked for you. But I will attempt to explain the process better.

When you run jscal, you need to take note of the numbers when you are calibrating the centre position for your axis. While it is running, it will ask for you to move the stick to the minimum, centre, then maximum, take note of the centre number, it is in the hundreds for me with my joystick.
When you create the joystick.cal file, look for numbers very close to those you observed while doing the centre calibration, they should appear as a pair, identical or very close.
This pair of numbers, you reduce the first one by a few points, and increase the second by a few points for the desired axis (I chose to decrease by 6, and increase by 6, worked for my joystick).
The first number is your number of axis, and your centre number for the first axis (0) should be about the fourth and fifth in the set, which are zero's in your output.

Sample of my output, you can see the similar numbers that I change.
jscal -s 6,1,0,**124,124**,10129331,9586688,1,1,**134,134**,8800894,7669350,1,0,**149,149**,5965050,7158060,1,0,107,107,6795627,7456313,1,0,0 ,0,536854528,536854528,1,0,0,0,536854528,536854528 /dev/input/js0

The changed set for axis 0, 1 and 2 (aileron, elevator, rudder).
jscal -s 6,1,0,**118,130**,10129331,9586688,1,1,**128,140**,8800894,7669350,1,0,**143,155**,5965050,7158060,1,0,107,107,6795627,7456313,1,0,0 ,0,536854528,536854528,1,0,0,0,536854528,536854528 /dev/input/js0

Hope this helps.  I can do more detailed with screen shots if needed.

---

### Post by 4rk3typ3 on 2010-06-17
Excellent, thank you very much :D. It seems to have worked to resolve most of the issue, this controller is incredibly sensitive so I'll keep playing with it but so far I've played in mupen64plus and snes9x without issue (configuring buttons was a pain in snes9x...). jscal was reporting 28 axes but only parsing 16 which would give an error relating to too many axes specified. The output I provided was what I was using after I modified the source of jscal ( MAX AXES was defined for 16 instead of 28 ) Which worked quite well, it got rid of the errors I was experiencing and allowed me to use the -c with jscal to actually calibrate the controller (albeit...not a very good job of it). 

I would post the source file that I edited but honestly it was a minor patch to make me feel all cozy (and to fix the seg fault/bus error)

If anyone would like to apply the "patch" themselves, download the joystick source from [http://archive.ubuntu.com/ubuntu/pool/universe/j/joystick/joystick_20051019.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/universe/j/joystick/joystick_20051019.orig.tar.gz")

extract it and use your favorite editing program (I prefer nano) to open the file jscal.c

Once you're in there, look for the line (should be pretty close to the top) 
```
#define MAX_AXES 16
```
and change it to this
```
#define MAX_AXES 28 //or however many axes you want
```

run the installation just like normal from there (instructions are included in the source). Again, this doesn't change anything...just gets past the seg fault (32-bit) or bus error (64-bit) and allows you to calibrate, but you'll still most likely have sensitivity issues and so following Sepius' advice will get you the rest of the way there. Hope this helps someone :D

*Note: If using this source package, unless you specifically install it in a way that lets you execute it as a command, you'll have to run ./jscal <options> <device> from the source directory after installation.

P.S. Forgot to mention, what Sepius' did there is make the Axes configuration for 0-3 (analog sticks) at the beginning have a null zone to allow a little play in the sticks. By default jscal liked to stick all the stick configurations at the end and by moving them to the beginning it modified the sticks. Another thing to note about jscal's calibration file is that if the section starts with a 1, it expects 5 parameters after it before the next axes begins (IE: 1,0,124,124,10129331,9586688) however, if it starts with a 0, it only expects 1 thing after it (IE: 0,0) so watch for that when you're working with your calibration file.

---

### Post by T4b on 2011-02-10
I'm not sure how exactly you got it to work, do you both use this  slightly modded version of jscal? Or is there an other way around this  *** bus error?

I tried to compile jscal with a maximum of 24 axes, but it doesn't change anything, I get the same bus error still...
Also 4rk3typ3 said there were instructions how to install in the sources, but I couldn't find any, so I just used "make".

All in all I would like some clear, easy instructions on what to do to get the controller to work.

---

### Post by T4b on 2011-02-20
Push.
I'm still interested in some more precise information on what to do.

---

### Post by rpstulk on 2011-02-24
I've been having this problem for a while.  Can't wait to try this patch for jscal.

---

### Post by T4b on 2011-03-02
> **T4b said:**
> I'm not sure how exactly you got it to work, do you both use this  slightly modded version of jscal? Or is there an other way around this  *** bus error?

I tried to compile jscal with a maximum of 24 axes, but it doesn't change anything, I get the same bus error still...
Also 4rk3typ3 said there were instructions how to install in the sources, but I couldn't find any, so I just used "make".

All in all I would like some clear, easy instructions on what to do to get the controller to work.
.

---

### Post by T4b on 2011-04-02
Push

---

