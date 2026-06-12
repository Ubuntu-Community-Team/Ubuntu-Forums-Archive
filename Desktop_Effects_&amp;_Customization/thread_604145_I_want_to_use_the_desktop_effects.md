---
title: "I want to use the desktop effects"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by xsabrewulf on 2007-11-05
I have tried a few things, I have an X1900XT

I have tried installing compiz and like the desktop goes to like a slideshow... very slow

I have an AMD 2.8GHZ Dualcore 2gb of ram, this should NOT be slow.


How can I get the desktop effects working? i really want the wobbly windows

---

### Post by carlinuxlearner on 2007-11-05
First we need to know exactly what card you have so. In a terminal window type "lspci | grep VGA" (to open up a terminal window (Applications>>Accessories>>Terminal).

C@RL

---

### Post by xsabrewulf on 2007-11-05
03:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary)


that is what it says

---

### Post by xsabrewulf on 2007-11-06
can anyone give me some advice from that info i got from the terminal?

---

### Post by rsambuca on 2007-11-06
Whoa, it is considered very poor etiquette to bump your posts so quickly.  Perhaps wait a day or use the IRC channels if you require immediate assistance.

---

### Post by Wartz on 2007-11-06
I have a ATI radeon x1950pro graphics card. What I did to enable the effects was first installing the restricted drivers.
```
sudo apt-get install xorg-driver-fglrx
```

I edited my xorg.conf to enable composite
```
sudo gedit /etc/X11/xorg.conf
```
Change 
```
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```
to read
"Composite"	"1"

I then installed XGL
```
sudo apt-get install xserver-xgl
```

and rebooted. Bingo

Hope that helps.

---

### Post by staticvoid on 2007-11-06
This might make that proccess easier:
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb")

Envy sets up nvidia and ati drivers automatically. click [here]("http://albertomilone.com/nvidia_scripts1.html") to learn more.

then if you are running ubuntu 7.10. right click to change your desktop background, choose the effects tab and set it to custom. then download compiz settings manager from synaptic and tweak away :D

sv

---

### Post by xsabrewulf on 2007-11-06
OK


I did everything you said in order... it reloaded up Ubuntu 7.10 (keep in mind I already had restricted drivers enabled and it was checked and said "in use")

and EVERYTHING is VERY VERY VERY slow, some graphic errors such as the volume icon is all messed up... everything is slowww... Like when I scroll down a webpage i see BAD tearing.

When I go to enable the desktop  it says "Desktop effects could not be enabled"


has ati released some drivers recently or anything? I installed these drivers when 7.10 final came out.

---

### Post by xsabrewulf on 2007-11-07
Well ive read other posts and I can not figure this out. I am very new to linux...

---

### Post by xsabrewulf on 2007-11-07
Anyone?

---

### Post by jimerickso on 2007-11-07
you could try installing the new ati driver 8.42.3 it uses aiglx so you wouldn't have to mess with xgl. it might help.

---

### Post by xsabrewulf on 2007-11-08
whats the command to uninstall the current video card drivers and install the new ones?

---

