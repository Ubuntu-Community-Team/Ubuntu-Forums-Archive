---
title: "[SOLVED] Dual Screen (Extended) with Inspiron 1420 (Intel GMA x3100 graphics)??"
date: 2008-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jonathanmotes on 2008-08-08
Has anyone gotten dual monitor with extended screen to work with Intel GMA x3100 graphics? If so, could you provide your xorg.conf file please?

Thanks!

---

### Post by sciurus on 2008-08-09
See [http://ubuntuforums.org/showthread.php?t=617934]("http://ubuntuforums.org/showthread.php?t=617934")

Note that you can now use the "Screen Resolution" tool to setup dual screen instead of the xrandr command

---

### Post by ThaRabbit on 2008-08-11
> **sciurus said:**
> See [http://ubuntuforums.org/showthread.php?t=617934]("http://ubuntuforums.org/showthread.php?t=617934")

Note that you can now use the "Screen Resolution" tool to setup dual screen instead of the xrandr command

I have a HP Compaq 6720s with Intel x3100 graphics, the "Screen Resolution" tool worked fine for me. 

Note that you may have to attach the external screen, THEN boot your system. It was slightly buggy for me while attaching the external panel during live ubuntu.

Proof:
[[IMG]http://img147.imageshack.us/img147/542/img2922ei1.th.jpg[/IMG]](http://img147.imageshack.us/my.php?image=img2922ei1.jpg)

---

### Post by jonathanmotes on 2008-08-12
Thanks for the replies everyone! I will be trying both methods soon and will report on my success. The last time I tried the "Screen Resolution" tool I was only able to get a cloned view, but that was a while ago. Maybe some bugs have been fixed since then.

---

### Post by ianchai on 2008-08-25
> **jonathanmotes said:**
> Thanks for the replies everyone! I will be trying both methods soon and will report on my success. The last time I tried the "Screen Resolution" tool I was only able to get a cloned view, but that was a while ago. Maybe some bugs have been fixed since then.

I just installed Ubuntu 8.4 on my Inspiron 1420 and cannot get it to *not[I]clone the screen. Even when the Screen Resolution tool shows the external monitor on its side and I click OK, it [I]still* clones the screen!

Any help would be appreciated... I'm a long-time UNIX user, but I'm new to Ubuntu.

---

### Post by jonathanmotes on 2008-08-25
> **ianchai said:**
> I just installed Ubuntu 8.4 on my Inspiron 1420 and cannot get it to *not[I]clone the screen. Even when the Screen Resolution tool shows the external monitor on its side and I click OK, it [I]still* clones the screen!

Any help would be appreciated... I'm a long-time UNIX user, but I'm new to Ubuntu.

I got it to work the other day on my Inspiron 1420. However, I was never able to get larger than a 2048 by 2048 virtual area - which means the max resolution for each screen will be something like 1024x768 (Or, in my case I used 1280x800 and 720x540 - I believe). Supposedly, if you turn off compiz you can get a larger virtual area, but I didn't have much success.

The Screen Resolution tool will work once the virtual area is defined in your xorg.conf file as long as your screen resolutions added together don't exceed the max. virtual area.


The process was something like this for me:
1. Boot with second screen attached.
2. Replace screen section in your /etc/X11/xorg.conf file with this (you might need to change the virtual size):
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
            Depth           24
            Virtual         2048 800
        EndSubSection
EndSection
```

I used 2048x800 for my virtual area so that I could have 1280x800 for the laptop and 720x540 (extended to the right) for my other CRT monitor. (since 1280+720=2000, I probably should have just used 2000x800 for the virtual size).

3. Restart X (Ctrl+Alt+Backspace)
4. Log back in and use the Screen Resolution tool to configure your layout. Remember the tool won't work if your resolutions exceed your virtual area.

Hope this helps!

---

### Post by 1qwik7 on 2009-04-30
Hey guys, sorry for the newb bump but im having trouble with this same problem. Long story short, i was a windows user since 2001 and only now have i stumbled upon ubuntu because i didnt know the computer came with it (lol yeah im a computer newb as well). 
 
So anyway i kept my original monitor from my old computer, and now want to join it with the new computer (dell inspiron 530) running ubuntu 8.04.
 
I bought a VGA splitter and quickly installed it.
 
Here is where it gets weird. When i installed the 2 monitors to the splitter, i got 2 displays using my ORIGINAL resolution settings, which were like 1440x900 or something like that. 
 
Going on youtube like an idiot, i followed some steps to setup a dual monitor but that was the incorrect tutorial i was supposed to be following and screwed up my original setting.
 
Now im maxxed out at a 800x600 resolution for BOTH monitors and i cant even get 1 monitor to go back to 1440x900 if i unplug either one from the splitter.
 
My graphics card is (integrated intel GMA x3100) and i did a couple of quick searches on google and see it is possible to have it setup.
 
For those wondering what monitors i have, i have 2 dell se198fwp which are 19" widescreens.

Please help me, i am a total noob to linux and i have read alot of stuff here but i dont understand it. Please guide me the retarded way and ill paypal you some bucks?? :P

---

### Post by jonathanmotes on 2009-05-01
Hi,

I'm not quite sure what you are trying to do. Could you explain a little more please?

I know with a VGA splitter, both screens will have to have the exact same resolution because there is no way for the computer to detect the hardware differences. The best choice for dual monitors is to buy an additional graphics card or a graphics card with two outputs. 

To get your computer back to normal, try running this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot.

By the way, compiz (your desktop effects manager) only supports a virtual resolution of 2048x2048. In other words, if you want one monitor to extend to the right or left of your primary monitor, you will either have to:
1. Turn compiz off, or
2. Run one or both monitors at a low enough resoluton so that the horizontal # of pixels of each monitor added together is less than or equal to 2048. For example: run both monitors at 1024 x 768 (1024 X 2 = 2048 ).

Just ask if you have more questions! I'm glad to help without money :)

---

### Post by jonathanmotes on 2009-05-01
Here are the instructions for a true dual monitor setup with extended desktop. This assumes your monitors are 1440 x 900 resolution and each monitor is connected to a separate VGA output on your computer.

First:
Turn off compiz:
Right click on the desktop, select "Change Desktop Background", click
"Visual Effects", then click the "none" option.

Second:
Open your xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```
Add to/Edit the display subsection to include the virtual area. For example:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2880 900
	EndSubSection
EndSection
```

Third:
Open the Screen Resolution tool (System, Preferences, Screen Resolution) and position the screens where you want them.

This should work - I know it does with Intrepid and Jaunty (8.10 and 9.04).

---

### Post by robin.nightingale on 2009-06-16
Does that mean that i could enable Desktop effects in dual screen mode ?

Sorry if that sounds a bit naive, but iam mac user and iam not so experienced with linux, but willing to learn and change my runnig os. Thanks a lot 

This is my Graphic Card:

Intel GMA X3100:

  Chipsatz-Modell:	GMA X3100
  Typ:	Monitor
  Bus:	Integriert
  VRAM (gesamt):	144 MB
  Hersteller:	Intel (0x8086)
  Geräte-ID:	0x2a02
  Versions-ID:	0x0003

---

### Post by jonathanmotes on 2009-06-16
> Does that mean that i could enable Desktop effects in dual screen mode ?
Only if your virtual resolution is less than 2048. See post #8 for an explanation of what that means. Compiz is the desktop effects manager if you were confused about that.

---

### Post by OwnName on 2009-09-08
To enable virtual resolution bigger than 2048, follow the instructions to fix the mesa bug, as suggested by Ludovico Cavedon (thanks!):

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146298](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/146298)

briefly, for impatients, what I did on Ubuntu 9.04 Jaunty 64-bit, hp550 and obviously Intel GMA x3100:

1) System > Administration > Software Sources, add both Ludovico's Personal Package Archives entries:
deb [http://ppa.launchpad.net/cavedon/ppa/ubuntu](http://ppa.launchpad.net/cavedon/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/cavedon/ppa/ubuntu](http://ppa.launchpad.net/cavedon/ppa/ubuntu) jaunty main
and accept the warning.

2) Authenticate the PPA:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 426FF7FA

3) Update and install the patched mesa packages:
sudo apt-get update
sudo apt-get install | grep mesa
sudo apt-get install mesa-common-dev mesa-utils libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa

4) Shut down, connect the second monitor and start it up again.

5) Now my virtual resolution is 2560 x 1024:
sudo gedit /etc/X11/xorg.conf

        SubSection "Display"
		Virtual	2560 1024
	EndSubSection

---

### Post by jonathanmotes on 2009-09-08
> **OwnName said:**
> To enable virtual resolution bigger than 2048, follow the instructions to fix the mesa bug, as suggested by Ludovico Cavedon (thanks!):


Wow...I always thought that was a compiz limitation. Thanks for putting this out there!

---

