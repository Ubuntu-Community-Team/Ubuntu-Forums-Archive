---
title: "microphone does'n work on Dell Inspiron 640m"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by neutrino82 on 2007-07-01
I tryed to use an external microphone on my 640m with Ubuntu Festy but seem it doesn't work at all. I have ALSA driver 1.0.13-3ubuntu1 installed. I wish anybody could help me to fix this...:)

---

### Post by Grigorius on 2007-07-01
Try fidling with system/proprieties/sound a bit to see if you can get it to work.

---

### Post by neutrino82 on 2007-07-02
I've already tried this but it doesn'help. I also tried to change alsamixer settings but nothing changes. I still can't record sound from the external mic. I wonder where the problem is.

---

### Post by Suzan on 2007-07-03
I've got a Dell Inspirion 6400.

I've noticed, the the mic don't work with Gnome-Apps like gnome-recorder or ekiga.

BUT the mic works without hassle with audacity or skype.

Have you tried it with audacity?

---

### Post by punkybouy on 2007-07-04
On the top panel right click on the speaker icon and select "Open volume control"  Then in the window that pops up you should have two tabs: "Playback" and "Capture".  Make sure your mic is not muted in these and in the "Capture" tab make sure it is not muted here and push the volume sliders to maximum. That should work.

---

### Post by Caro_CR on 2008-02-12
> **punkybouy said:**
> On the top panel right click on the speaker icon and select "Open volume control"  Then in the window that pops up you should have two tabs: "Playback" and "Capture".  Make sure your mic is not muted in these and in the "Capture" tab make sure it is not muted here and push the volume sliders to maximum. That should work.

I've already tried everything... my mic does not work, I have a Dell INspiron 640 m too...

When I try to make a test on preferences/sound/
I got this:

It failed...  «gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat»

---

### Post by Paul S on 2008-02-13
This worked here on KDE .. in a terminal:

~$ amixer set Capture toggle

and test with

~$ arecord -f cd out.wav

and to test

~$ aplay out.wav

---

