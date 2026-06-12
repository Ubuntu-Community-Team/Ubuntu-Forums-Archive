---
title: "White Screen after enableing Desktop Effects"
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by pat23_2007 on 2007-08-17
Hi 

I clicked Enable Desktop effects and then it just went to a white screen, i let it sit for awhile nothing happened, turned off the pc and rebooted Ubuntu and got pasted the user screen but once it loaded it just wented white screen again. Any way to fix this problem?

Specs are: 

Custom Built PC
AMD64 Athlon +3000 2.0GHz
1.50 GB Ram

Ubuntu Version: Feisty 7.04 AMD64

Dual Booted with Win XP Home.

---

### Post by silent1643 on 2007-08-17
has to do with your video card... what are your specs on video
most ati and nvidia cards require additional work

---

### Post by pat23_2007 on 2007-08-17
> **silent1643 said:**
> has to do with your video card... what are your specs on video
most ati and nvidia cards require additional work

Video Card Specs:

Name: WinFast PX360
Chip Type: GeForce PCX 5750
Mem: 128MB

---

### Post by FuturePilot on 2007-08-18
Did you install the driver with the Restricted Driver Manager?

---

### Post by pat23_2007 on 2007-08-18
> **FuturePilot said:**
> Did you install the driver with the Restricted Driver Manager?

Uh no i knew i was supposed to but i forgot to, is their anyway to fix this with out having to reinstall ubuntu?

---

### Post by pat23_2007 on 2007-08-18
Ok guys i have tried all i know and i still can't find a way to fix this, any help or am i just at a lost?

---

### Post by FuturePilot on 2007-08-18
Just install the driver and reboot. Then try enabling the Desktop Effects.

---

### Post by pat23_2007 on 2007-08-18
> **FuturePilot said:**
> Just install the driver and reboot. Then try enabling the Desktop Effects.

I can't every time i log in to Ubuntu its just a white screen now, i can only log on under a Failsafe Terminal session. 

So how would i go about doing this from just the terminal?

---

### Post by FuturePilot on 2007-08-18
Can you log into a Failsafe Gnome session and then disable the Desktop Effects?

---

### Post by pat23_2007 on 2007-08-18
> **FuturePilot said:**
> Can you log into a Failsafe Gnome session and then disable the Desktop Effects?

Nope, just comes up as a white screen too.

---

### Post by Gerwin on 2007-08-18
I dont realy no a solution but

I have had a simeler problem but i could see my mouse,

so i remeberd my dektop whit menu and turnt desktop effects of blind

(I hope you can read my English)

---

### Post by pat23_2007 on 2007-08-18
> **Gerwin said:**
> I dont realy no a solution but

I have had a simeler problem but i could see my mouse,

so i remeberd my dektop whit menu and turnt desktop effects of blind

(I hope you can read my English)

I can see my mouse too, but i don't get what you mean on the other stuff.

---

### Post by FuturePilot on 2007-08-18
Ok, it's possible but will be a little more difficult. I'm assuming you have a Nvidia card right? In the terminal do ```
sudo apt-get install nvidia-glx
```
Then you'll have to edit your xorg.conf file. So do ```
sudo nano -w /etc/X11/xorg.conf
```
Go down to the device section and where it says ```
driver   "nv"
``` change the "nv" to "nvidia". Also add these options to that section as well
```
  Option          "AddARGBVisuals"        "True"
  Option          "AddARGBGLXVisuals"     "True"

```
Then Ctrl+x to save, press Y then hit Enter.
Then reboot and you can login normally.

---

### Post by pat23_2007 on 2007-08-18
Ok thanks that worked but now my screen resolution can only go up to 800X600 when before i had it at my standarded 1440X900 how do i go about getting back up to the normal screen res's?

---

### Post by mattaphore on 2007-08-30
I have the same problem, except my computer has a ATI Radeon x200 card. I can access the terminal if I boot in recovery mode, or if i boot in failsafe terminal...

I'm a total n00b when it comes to Linux and i've been searching of ways to either get my Desktop Effects working or just removing them completely so I can see something other than a white screen again.

:( any ideas?

---

### Post by gogogadget on 2007-09-08
I have the exact same problem. I am using ubuntu 7.04 Faisty Fawn. The curious thing is that ubuntu is still working underneath this white screen. I have marked positions on the screen where logoff icon on the top panrl and restart one that button is pressed. So I can at least restart ckeanly. I tryed sudo dpkg-reconfigure -phigh xserver-xorg. This did not fix the problem.

I would like to use sudo spt-get remove <package name> or similar. I can get it to terminal mode to issue linux commands but I dont know what to do.

I dont believe a reload of the driver will affect anything. I am using a nVidea Ge Force 6800

---

### Post by gogogadget on 2007-09-10
I had the same problem but my solution was quite simple. I hope this helps.

Log in to recovery mode and when it is finished you will be at the command prompt and logged in as root.

change directory 

cd /etc/X11

create a backup of the file we are going to alter
cp xorg.conf xorg.conf.backup

use you favorite editor and edit xorg.conf
gedit xorg.conf

looking through the file you might see Load	"glx"
simply comment this line out be putting a hash (#) in 1st column of the line so it reads
#	Load	"glx"

reboot

and all should be ok

---

