---
title: "GforceTi4200"
date: 2005-05-27
forum: Gaming &amp; Leisure
---

### Post by catastrophee on 2005-05-27
I need to install this card and im not sure how to do it from the terminal ive read some threads and just couldnt catch on.

---

### Post by catastrophee on 2005-05-27
The only thing ive done so far is downloaded this from the synaptic command 

NVIDIA binary XFree86 4.x/X.Org driver development files


Also to let you guys know now im going to need help installing my motherboards agp 8x drivers as it is not working on my windows xp and this is the main reason for switching over to linux!! 

Lets get the nvidia problem fixed first then we will focus on getting my machine to run on agp8x

---

### Post by Seth on 2005-05-27
The Ti4200 isn't AGP 8x compatible.

---

### Post by catastrophee on 2005-05-27
Well my TI is 8x compatable because ive ran it on 8x before and it says 8x right on the box

---

### Post by Seth on 2005-05-27
[QUOTE=catastrophee]Well my TI is 8x compatable because ive ran it on 8x before and it says 8x right on the box[/QUOTE]
 Ah, you have one of the redone ones.

Read this then: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

All you'll need is nvidia-glx and Ubuntu should do the rest.

---

### Post by catastrophee on 2005-05-27
thats what ive been reading from the start but i just dont know what to write in the terminal ? ive tried "apt-get install geforce4 " and every possible name my video card would be called.... all wrong syntax errors...

---

### Post by gil-galad on 2005-05-27
apt-get install nvidia-glx
sudo nvidia-glx-config

---

### Post by catastrophee on 2005-05-27
I did apt-get install nvidia-glx and it said i already had it 

then i did the second line and then i enabled it now im restarting!

---

### Post by catastrophee on 2005-05-27
I need the code to test to see FPS what is it again ?

---

### Post by drummer on 2005-05-27
[QUOTE=catastrophee]I need the code to test to see FPS what is it again ?[/QUOTE]
 glxgears
- OR -
fgl_glxgears (actually, this one might only be for ati cards, sorry)

---

### Post by catastrophee on 2005-05-27
glxgears
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.


Does this mean its not installed ?? 

How do i install em....

---

### Post by catastrophee on 2005-05-28
ubuntu wont start up now it just loads like normal with the black screen after i select to boot linux and then goes black. 

I got a message one time and it was something X. It failed to work and it showed me 2 logs of what went wrong. 

Im guessing it has to do with the nvidia driver i installed..... well any suggestions ?


Also i have an off topic question about 64bit systems.... what are they and is it related to the motherboard ? Im buying a new motherboard so i just want some things to look out for also if i put these HD's on the new mobo will they work 100% fine and no data loss ?

---

### Post by catastrophee on 2005-05-29
I guess my ubuntu system is skrewedd im going to have to re-install.... umm i also wanna transfer the HD to a new motherboard is that possible ... ubuntu loads up and says " system critical temperature reached 120C system shutting down... and this is the screen it loads after GRUB.

---

