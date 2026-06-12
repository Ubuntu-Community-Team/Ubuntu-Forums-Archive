---
title: "Beryl problems + problem with movie playback..."
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by tyboon on 2007-05-04
I have installed beryl on my gnome ..it works fine except two things..

a)When i watch a film after a while my screen goes black..if i moone my mouse then it comes back but its a bit annoying...What can i do about it...?

b)The rain and snow effect doesnt work....any suggestion?

Thanx guys for helping me out on this too....:)

---

### Post by aidanr on 2007-05-04
i used to have that problem as well with videos even with the screensaver and power management disabled so i commented out "option dpms" in my xorg.conf and that took care of it (probably not a good idea for a laptop, or if you like monitor power management)

and the rain and snow effect i'm not too sure about, i think the rain effect used to require a video card with pixel shaders or something and the snow effect needs the png plugin to be activated afaik so check those

---

### Post by tyboon on 2007-05-04
how do i do that....i mean about commeniding those out in the xorg..?Can you tell me how...?
You think it will work or it will mess up my desktop...?
Thanx....:KS

---

### Post by aidanr on 2007-05-04
it won't mess up your desktop, copy/paste the following in a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup && sudo gedit /etc/X11/xorg.conf
```
go to Section "Monitor" and put a # before Option "DPMS" so it looks like:
```
#Option "DPMS"
```
save and exit and hit crtl+alt+backspace to restart X (save anything you have open before restarting X because it will close all your open programs)

---

### Post by tyboon on 2007-05-04
thanx Bro...hope it will work:) 
I appreciate it...Can you check something else for me too and give your opinion...?
Check on my threads for the cannon printing issue i have...I haven t short this out over a month now..:confused: 
Thanks again...

---

### Post by tyboon on 2007-05-07
Unfortunately that didnt work ...too bad..I start a movie and after a while tha screen goes black...?
may be i did something wrong..justa in case for everyone to see...

> Section "Monitor"
	Identifier	"Generic Monitor"
       #Option 		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60

Maybe the sentences allignment is wrong..?
I hope someone gives me some help..I heard it is a wide problem with Beryl...
Thanks you all guys..
:)

---

### Post by tyboon on 2007-05-29
I tried all this....:(
still any kind of video in widescreen  and the screensaver just turns black after something like 10 min period of time...
So anybody knows something?May be i am doing something wrong?
Thanks....

---

### Post by kronepils on 2007-05-29
How is your powermanagement settings?
System->Settings->Power Management (I think, my menu is in Danish...)

There you should be able to disable screensaver/power savings. 

Good luck!

---

### Post by pingpongboss on 2007-05-30
i found that using totem-xine instead of totem-gstreamer will make the Totem Movie Player work well under beryl.

---

### Post by magnusvv on 2007-06-09
I dug this thread up looking for a solution to my totem/beryl problem as well.  The totem-xine solution worked for me.  Thanks!

---

### Post by simosx on 2007-06-16
It's a known bug. You can use a workaround for now until it gets fixed upstream by redirecting the video output to a difference output device.
See [http://simos.info/blog/archives/594](http://simos.info/blog/archives/594) for instructions on Totem (gstreamer) and VLC.

---

