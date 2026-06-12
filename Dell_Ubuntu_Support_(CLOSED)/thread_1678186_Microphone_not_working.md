---
title: "Microphone not working"
date: 2011-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by prasanth020 on 2011-01-29
My dell laptop - 'Inspiron 1564' external and internal microphone is not working please give a solution please

---

### Post by clasificados on 2011-01-30
> **prasanth020 said:**
> My dell laptop - 'Inspiron 1564' external and internal microphone is not working please give a solution please


try this
in terminal logged in as root

cat /dev/dsp > testfile.out


then

cat testfile.out

hear anything?

also install alsamixer via command line and make sure volume controls are all they way up especially mic

---

### Post by Jimtheplanner on 2011-01-30
Another option maybe click to open the sound icon from the top panel then click to open sound preferences and open the "input tab" of the control panel then make sure the "mute box" is unchecked give it a try... You can also change the mic inputs I use Microphone 2 for my USB webcam and turn the input volume up. Also, if you watch the input volume meter you will see it move with as the mic detects a sound source 

Jim

---

### Post by prasanth020 on 2011-01-30
> **Jimtheplanner said:**
> Another option maybe click to open the sound icon from the top panel then click to open sound preferences and open the "input tab" of the control panel then make sure the "mute box" is unchecked give it a try... You can also change the mic inputs I use Microphone 2 for my USB webcam and turn the input volume up. Also, if you watch the input volume meter you will see it move with as the mic detects a sound source 

Jim
Thank you for your response . I checked already in settings but in the settings i can't found any connector.

---

### Post by prasanth020 on 2011-01-30
> **clasificados said:**
> try this
in terminal logged in as root

cat /dev/dsp > testfile.out


then

cat testfile.out

hear anything?

also install alsamixer via command line and make sure volume controls are all they way up especially mic
Thank you for replay. In the settings i tried to up the mic's  volume control but it not working and no connector found in the settings . Please give me a solution

---

