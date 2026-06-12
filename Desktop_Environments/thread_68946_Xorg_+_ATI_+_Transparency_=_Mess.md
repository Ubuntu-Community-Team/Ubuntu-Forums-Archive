---
title: "Xorg + ATI + Transparency = Mess"
date: 2005-09-24
forum: Desktop Environments
---

### Post by cypher35 on 2005-09-24
howdy, i'm relatively new to linux, but i know my way around the command line from past experiance with osx.

I've been trying to get transparency to work on my system and have gotten some weird and frustrating results.  Here's my setup:

**Kubuntu Release:** 2.6.10-5-amd64-generic
**KDE version:** 3.4.0
**Xorg version** 6.8.2
**Graphics Card:** ATI AiW 9700 Pro. (obviously bought before deciding to use linux)

After following a simple tutorial in these forums to get the graphics acceleration to work, i decided to tackle the transparency settings.  I finally figured out that i need to add the following to xorg.conf to get it to work:
```
Section "Extensions"
	Option	"Composite"	"Enable"
EndSection
```
I then refreshed the config using *ctrl+alt+backspace*, and was treated to a very broken, artifact ridden, messed up interface wich took me a while to restore because the text was incomprehensable.

I was wondering what i've done wrong, and if it has something to do with the fact that i have an ATI card in my system.

---

### Post by fordfan753 on 2005-09-24
Are you using the latest version of the ATI drivers? ATI drivers still leave a lot to be desired, but the latest version should help.

---

### Post by cypher35 on 2005-09-24
i was told to stay away from the official ATI rpms and use the one provided by ubuntu...

i'll give it a try and see if i have any more luck.

---

### Post by JLTB on 2005-09-24
The latest ATI binary installer (.RUN file, NOT .rpm) installs easily (compared to it's predecessors) .... heh provided you have a whole wack of compiler tools.

Just off the top of my head you will need to go 'sudo apt-get install linux-headers-2.X.X-X build-essentials gcc' maybe get lots more.  (PS: use 'uname -r' to determine your kernel version to install the correct headers, for instance I use breezy so I installed 'linux-headers-2.6.12-8-386').

In my experience the new drivers are quite a bit better, but on my ATI 9600XT there were artifacts everywhere too (with the comp manager).  Check out the Gentoo Wiki for more help on this sort of thing.

Alas, my friend's nvidia 9600GT will make shadows and transparency far better than my ATI card for a long time to come (i fear).

---

### Post by fordfan753 on 2005-09-24
[QUOTE=cypher35]i was told to stay away from the official ATI rpms and use the one provided by ubuntu...

i'll give it a try and see if i have any more luck.[/QUOTE]
I don't know much about ATI drivers, I thought they might come as a bzipped installer or something....

---

### Post by cypher35 on 2005-09-25
[QUOTE=JLTB]The latest ATI binary installer (.RUN file, NOT .rpm) installs easily (compared to it's predecessors) .... heh provided you have a whole wack of compiler tools.[/QUOTE]

where might i find this binary installer?

---

### Post by cypher35 on 2005-09-25
nevermind, i found the file and managed to install the  8.16.0.2 ati driver (or something like that), but transparency has not improved at all.

---

### Post by getaceres on 2005-09-27
[QUOTE=cypher35]nevermind, i found the file and managed to install the  8.16.0.2 ati driver (or something like that), but transparency has not improved at all.[/QUOTE]
To get transparency working at a good speed, you need to accelerate the Render extension. The only driver that accelerates that is the NVidia binary driver.
With any other driver you are going to have very poor performance.

---

### Post by cypher35 on 2005-09-27
Thanks, i guess i'll have to either wait for a new ati driver to come along, or purchase an nvidia card.

---

