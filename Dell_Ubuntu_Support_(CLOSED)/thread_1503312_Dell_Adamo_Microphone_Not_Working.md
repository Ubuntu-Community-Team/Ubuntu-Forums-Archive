---
title: "Dell Adamo Microphone Not Working"
date: 2010-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hlainchb on 2010-06-06
Hi Folks,
Just installed 10.4 on my new Dell Adamo 13 and everything works perfectly except the built in mic.  I have tried many things based on threads here including digging around the kernel repo looking for clues but I wonder if someone here can help.  Sounds works fine, just the mic is not working at all.  

I have tried alsamixer and it shows three capture devices, "Capture", "Capture 1" and "Digital Mic".  I suspect (but could be wrong) that I need to set "Digital Mic" as my capture device but although I can select the other two, I cannot select the "Digital Mic".

arecord -l produces this:

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

Any help is appreciated.
Thanks!
H

---

### Post by jasonbobasin on 2010-06-13
I'm having the same problem, haven't been able to find a fix yet.

---

### Post by chromax on 2010-10-02
Have the same problem with the adamo 13. The mic is also dead in XP 32bit. I already thought about a hardware problem, but it seems a driver thing.

---

### Post by hlainchb on 2010-10-03
I have mine working now.  All I did was uninstall and reinstall my pulse audio drivers.  Get the latest ones from their site.  Everything on my Adamo works perfectly now.  :-)

---

### Post by sagara on 2011-01-20
Here is what you do to fix this:

Open a terminal and type:

gksudo gedit /etc/modprobe.d/alsa-base.conf

this will open a text file, add the following line to the end of the file:

options snd-hda-intel model=dell-m6

close the text file and run this command:

sudo alsa force-reload

Your headphones and microphone should work now, enjoy!

---

### Post by jasonbobasin on 2011-04-30
Got it, I had to use
options snd-hda-intel model=dell-m6**-dmic**

to get the microphone to work.

---

