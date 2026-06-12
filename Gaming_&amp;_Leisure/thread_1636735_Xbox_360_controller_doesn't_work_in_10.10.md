---
title: "Xbox 360 controller doesn't work in 10.10"
date: 2010-12-03
forum: Gaming &amp; Leisure
---

### Post by aj_the_first on 2010-12-03
I've been an Ubuntu user since 8.10, and I am just now deciding to try Linux gaming.  I've been online upgrading the OS consistently since 9.04, and 10.10 is running flawlessly on my machine. (A four year old Toshiba Satellite with an AMD 64 dual core)

I am trying to use an xbox 360 controller on my machine, and it is recognized (lsusb lists it properly) but it controls nothing.  I've tried it on tuxcart, super tux2, and Armagetron Advanced.

I chose the xbox 360 controller because it is supposed to be plug-and-play with Ubuntu 10.10, but I if it wasn't for lsusb and a red LED on the controller, I wouldn't know it was plugged in.

Is it that these three games don't support controllers, or did I miss something?  Please help.
Thanks,
AJ

---

### Post by Zzl1xndd on 2010-12-03
Not sure with these games, but normally you have to configure the controller for each game. Most games have a section where you can change the control options.

---

### Post by aj_the_first on 2010-12-03
Yes, I tried that, but the games in no way recognize the controller.  I am an avid gamer, and I am an avid Linux user, just not a Linux gamer... I should be able to figure this out, but I can't.

---

### Post by aj_the_first on 2010-12-03
Update: I have now tried it on about 15 different games just to be sure, many flight sims, a few side scrollers and some 3d racing games.  Nothing recognizes the controller, either in the game or the configuration.
lsusb shows:
Bus 005 Device 007: ID 045e:028f Microsoft Corp. Xbox360 Wireless Controller

It really would be super to use it.  Anyone have any ideas where I should start?  I just can't seem to find a problem anywhere other than the fact that it just doesn't do anything work...

I tried the controller on my xbox360 just to make sure the controller is still working, and it is fine.

---

### Post by thatguruguy on 2010-12-03
I have a generic xbox 360 controller, but mine is wired rather than wireless. Have you tried a program like qjoypad to translate the the joystick movements and button pushes to keyboard mappings?

---

### Post by aj_the_first on 2010-12-04
Ah, see, now that was what I was curious about: a program needed to translate inputs.  I'll try that out.
I have a factory xbox 360 controller wired via USB.

---

### Post by aj_the_first on 2010-12-05
I've been trying to install QJoyPad, but it just won't happen.

I wasn't surprised, as this would've been my first time to successfully install a tarball.  I have tried to install tarballs at least 30-40 times with programs I really want, and have always done exactly as the install files say, and corrected any deficiencies that the errors tell me I have, but in the end it never actually installs correctly or at all, and has about half the time killed my OS and I have had to re-install the entire operating system.  So I won't mess with tarballs until I have backed up all my media and have about a week in my life where I won't need a computer.  I've never had a problem with a debian file in the last 4 years.  It just makes me wonder why anyone would write code that has to be compiled instead of writing a proper auto installer...  anyway, rant about tarballs complete...

I'm an IT professional by trade, but mostly networking and human interface products, so I'm not a total computer dolt, but linux core library stuff is beyond me.

I've already fixed a couple of the issues that the config file has told me, but now the config file is telling me that I need qt4.2 or higher, which I thought was default in Ubuntu 10.10:

andrew@Linus:~/Desktop/QJoyPad/qjoypad-4.1.0/src$ ./config
Error: you need at least Qt version 4.2 to use this program

Should I try installing QT4.2?  It is also a tarball, and a rather integrated-into-the-OS one at that...
Synaptic shows all the (non-developer) QT4 libraries are already installed.  Any other suggestions before I make an attempt and probably kill my computer again?  :(
Thank you

---

### Post by aj_the_first on 2010-12-05
Synaptic is showing that I have QT4.7.4 installed.  So is QJoyPad's config file not working properly?  Or it doesn't know what to look for?  Does anyone know what is happening and how to fix it?

I tried to just go forward and make install, but here is what I get for that:

andrew@Linus:~$ cd /home/andrew/Desktop/QJoyPad/qjoypad-4.1.0
andrew@Linus:~/Desktop/QJoyPad/qjoypad-4.1.0$ cd src
andrew@Linus:~/Desktop/QJoyPad/qjoypad-4.1.0/src$ make install
make: *** No rule to make target `install'.  Stop.
andrew@Linus:~/Desktop/QJoyPad/qjoypad-4.1.0/src$ 

And sure enough, the directory does not contain an install file.

I am assuming this is because the config file has to successfully run error free before continuing to the install.  And maybe config creates the install file after it checks and ensures the computer is configured correctly?

---

### Post by aj_the_first on 2010-12-05
Okay, I've verified my QT version.  (4.7.4)
I've unpacked and run config from the core directory exactly as the install file says to do, and regardless of how I download and unpack the tarball or reinstall QT, it is the same error.

I've done it a few times to ensure it is easily reproducible, and then submitted it as a bug to QJoyPad sourceforge page.

So, no xbox360 controller, nor QJoyPad.  :(
I want to play...

---

### Post by thatguruguy on 2010-12-05
It's a LOT easier to get qjoypad from [PlayDeb.net]("http://www.playdeb.net/updates/ubuntu/10.10/?q=qjoypad").  PlayDeb is a great resource for ubuntu-compatible games, generally.

---

### Post by aj_the_first on 2010-12-05
Thanks so much for the link.  Great stuff on that site.  I searched for a qjoypad debian file for about an hour before deciding to give the tarball a try...  How did this site never come up even once in all my google searching?
But there is a new problem:
qjoypad doesn't recognize the xbox360 controller.  Again...  I don't even know where to begin.  I've included a screen shot so you can see my USB xbox360 controller very clearly plugged in and recognized in terminal with lsusb, and qjoypad's error message telling me nothing is plugged in (updating the list as it recommends changes nothing)
[http://www.flickr.com/photos/aj_the_first/5236764478/](http://www.flickr.com/photos/aj_the_first/5236764478/)

Do you have any suggestions?

---

### Post by aj_the_first on 2010-12-07
I spent a few hours searching for ANY way to figure this out or any other way to get an xbox 360 controller working in Ubuntu.  I can't fand anything in this forum nor online. 
I was told that the flight SIM gl-117 should recognize the controller, but it doesn't either.  I am thinking that the xbox360 driver that ubuntu claims is default in the kernel is not updated/installed during online upgrade? 
Does anyone know how can I resolve this?  I just want to use a controller on my machine.  I've tried a few different USB controllers now and I get the same result on all of them: the controller is recognized as far as the USB list (lsusb) is concerned, but no game, nor QJoyPad recognizes any controller being plugged in.
 
Help anyone?

---

### Post by kdog_1914 on 2010-12-08
> **aj_the_first said:**
> Okay, I've verified my QT version.  (4.7.4)
I've unpacked and run config from the core directory exactly as the install file says to do, and regardless of how I download and unpack the tarball or reinstall QT, it is the same error.

I've done it a few times to ensure it is easily reproducible, and then submitted it as a bug to QJoyPad sourceforge page.

So, no xbox360 controller, nor QJoyPad.  :(
I want to play...

Late to the party, but I did find the solution for this.  You're running python-qt4 version 4.7.2  I thought the same thing initially. Run: ```
sudo apt-get install qt4-qmake
``` which will install qt4 and dependencies.  Probably more as well, but I'm going with what worked for the time being.  Once installed, you will be able to config/make/make install.  Once complete, run: ```
qjoypad --notray
``` which will give you a little window.  You should be able to follow the documentation on qjoypad's site from there.

I have yet to get the mappings to pass to armagetron but I'll pick it up again tomorrow.  If you make progress in getting the keys to pass to the game, let me know what worked.  Thanks

---

### Post by kdog_1914 on 2010-12-08
> **aj_the_first said:**
> Thanks so much for the link.  Great stuff on that site.  I searched for a qjoypad debian file for about an hour before deciding to give the tarball a try...  How did this site never come up even once in all my google searching?
But there is a new problem:
qjoypad doesn't recognize the xbox360 controller.  Again...  I don't even know where to begin.  I've included a screen shot so you can see my USB xbox360 controller very clearly plugged in and recognized in terminal with lsusb, and qjoypad's error message telling me nothing is plugged in (updating the list as it recommends changes nothing)
[http://www.flickr.com/photos/aj_the_first/5236764478/](http://www.flickr.com/photos/aj_the_first/5236764478/)

Do you have any suggestions?

It's not clear if you were able to install qjoypad by this post, so I'll take a stab at this too.

run:```
ls /dev/input/js*
```You should see something like: /dev/input/js0 or /dev/input/js1 etc.  If you get that far, qjoypad  should read it in order when you right-click on the window described in my last reply.  Let me know what you find.

---

### Post by aj_the_first on 2010-12-08
Oh, yes, I was able to install QJoyPad using the debian file on playdeb.com. Installed with no problems. Now I have the icon in the tray, but when I try to launch it, it just tells me that no controllers are plugged in. Check the picture that I linked on my flickr (I tried to insert it into to the post, but it kept coming up with a broken image)
Here is the image:
[http://www.flickr.com/photos/aj_the_first/5236764478/](http://www.flickr.com/photos/aj_the_first/5236764478/)
As you can see, QJoyPad is running and telling me that my controller is not plugged in, but terminal is showing the usb list with the xbox controller plugged in and properly recognized and labeled.
Thank you for your help. I really want to play some games. I'm not particular on which ones as I enjoy many, but I hate using the keyboard and mouse for gaming unless it is something like solitare, poker, or backgammon.
 
I see that you want me to list inputs of some sort in terminal (I do very basic stuff in terminal like changing file permissions and moving files in bulk and getting apps) I'll do that and let you know what happens. I'm at work right now, but I think I am about to skip the rest of the morning to head home and try to get this working...
 
UPDATE: Okay, I am a dolt. I see what the terminal code you asked me to use means: list, devices, input, joystick, any/all. :P Judging by what seems to be happening with my computer, I bet it will yield no results. I'll let you know.
If it yields no results, do you know where to go from there? Should I start a new thread with a much more specific statement of my problem at that point?
Thanks again for your help, 
AJ

---

### Post by aj_the_first on 2010-12-08
As I suspected, my computer has no idea what a joystick is:
Check it out:

andrew@Linus:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:028f Microsoft Corp. Xbox360 Wireless Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
andrew@Linus:~$ ls /dev/input/js*
ls: cannot access /dev/input/js*: No such file or directory
andrew@Linus:~$ ls /dev/input
by-path  event1  event3  event5  mice    mouse1
event0   event2  event4  event6  mouse0
andrew@Linus:~$ 

That is it for devices...  This is definitely where I have no idea how to proceed from here.  I can see that I am missing the actual js directory/folder, but ...  what can I do about that?   Should I start a new thread with a more detailed description of the problem?...  maybe I should search my newly identified problem in the archives first...

Again, thank you.  I can put my finger on something much more specific.  Now to solve it.

---

### Post by daniel_w93 on 2010-12-29
okay so when I put 

```
lsusb
```

my output is the following:

```
Bus 002 Device 003: ID 045e:028f Microsoft Corp. Xbox360 Wireless Controller
Bus 002 Device 002: ID 06a3:0109 Saitek PLC P880 Pad
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 001 Device 004: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

So the Xbox controller as well as my Saitek gamepad are recognized as usb devices...however, if I put 

```
ls /dev/input
```

the output I get is:

```
by-id    event0  event2  event4  js0   mouse0
by-path  event1  event3  event5  mice

```

so it shows only one Joystick...which would be my saitek pad, since it's working fine.
So somehow you'd have to make ubuntu realize that the usb device: Xbox 360 Wireless Controller is a joystick and make it appear as js1 in /dev/input....
but how do you do that????

---

### Post by daniel_w93 on 2010-12-29
just found something that might explain it...

if you're using the wireless controller and have this usb cable plugged into it...that you use for charging (just what i am doing) I have some bad news I think 

> Please note that using a wireless Xbox 360 controller with the Play&Charge USB cable will not work. The cable is for recharging only and does not transmit any input data over the wire.
from
[http://www.*****************/driver/articles/how-to-use-xbox-360-wireless-gaming-controller-on-ubuntu-10-10.html]("http://www.*****************/driver/articles/how-to-use-xbox-360-wireless-gaming-controller-on-ubuntu-10-10.html")
(WHAT THE HELL IS HAPPENING WITH THE LINKS!!!!? >:@ 
that would make sense...cause the controller isn't recognized on my windows system either using the original Microsoft drivers.

---

### Post by stefanadelbert on 2011-01-08
Bad news from [Ubuntu Documentation]("https://help.ubuntu.com/community/Xbox360Controller"):

> Before you begin I would like to point out that the Xbox 360™ does not use Bluetooth® for its wireless communication. If you have a wireless controller, you need to get an Xbox 360™ Wireless Gaming Receiver for Windows®. Don't worry, it works under Linux too, although there are a few quirks. All you need to do is to plug it in, as you would under Windows®, and it should behave similarly to the USB controller.

I thought that the controller used Bluetooth, but clearly not. Seems you need a [special 2.4GHz receiver]("http://support.microsoft.com/kb/933711?sd=xbox") to actually get data from a wireless XBox360 controller to a PC. The USB cable is used just for charging the controller and not for sending data from the controller to the PC.

---

### Post by fil_lif on 2011-01-11
are you using the xpad kernel driver? it's not great for 360 controllers.
if you haven't already tried it, xboxdrv is a highly configurable alternative (there's a few other dependencies too)
you can get the tarball at [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/) or add the repo, and check out this thread (by someone a lot smarter than me) [http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464) for a good step-by-step usage guide

---

### Post by wujj123456 on 2011-04-09
For the QJoyPad thing, there is a typo in their INSTALL.txt. 
./config won't work. It should be ./configure instead. 

I got it working perfectly with my wired controller. Hope that helps.

---

### Post by keltic dave on 2011-04-10
don't know why you would have to configure anything I use a 360 controller on 10.10 and I didn't need to install or config anything.

---

### Post by phoinx on 2011-09-28
> **kdog_1914 said:**
> 
```
sudo apt-get install qt4-qmake
```
```
qjoypad --notray
```


Worked for me! Thanks!

---

