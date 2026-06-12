---
title: "New ATI Drivers = no more desktop"
date: 2009-02-22
forum: General Help
---

### Post by 5oh on 2009-02-22
Ok,
  I've been battling random system hangs, freezes etc for the last 4 months. I have ubuntu installed on 2 different systems. One is a server I use at work and one is my media center PC at the house. Thankfully the server has worked wonderfully with nary a problem.

My media center PC has been anything but stable. I have reload it 4 or 5 times only to keep experiencing the same issues. It just randomly dies. I keep updating things hoping it will get better, (probably not the best idea, but I'm pretty much a Linux noob and don't really know what else to do), but things seem to stay the same. 

I had noticed while trying to play Torcs and some other games, that the screen tends to flicker. So, after searching the forum, I seen that ATI had released a new driver for my Radeon card. I installed it and BAM, when I played a video in Fullscreen the system locked up and was completely unresponsive. 

Sooooo I searched the forum, searched google for instructions on removing the new driver and reverting to the old, with out much luck. I found some information that I thought would do it, but since my desktop is completely white, with nothing available. No menu bars, background is gone and none of the shortcuts work. All I can do is kill x with ctrl + alt + backspace

WTF!!!

---

### Post by DagMan on 2009-02-23
hit ctrl-alt-f1 at the white screen.  This will give you a command line interface with a login prompt.  Login with your username and password, then try the following command at the prompt:
```
sudo aticonfig --initial
```
and reboot.  this may solve it.
-----------

if not, again get get the the comand line interface... ctrl-alt-f1, then log in. and try this:
```
sudo /etc/init.d/gdm stop
sudo killall -9 X Xorg
sudo apt-get remove --purge fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx xorg-driver-fglrx-dev libamdxvba1
sudo rmmod fglrx
sudo apt-get install xorg-driver-fglrx fglrx-kernel-source
```If you have a wireless connection then it won't be up without a gui, so you'de want to plug into a cable for connectivity to download the packages pulled in by the last command.

--------------

If you can't get things going still, edit the file /etc/X11/xorg.conf to use the open source driver so you have a working gui.  Again in the command line interface, log in and do the following:
```
sudo nano -w /etc/X11/xorg.conf
```and scroll down using the arrow keys until you get to a part that says 
```
	Driver      "fglrx"
```and change it to ```
	Driver      "ati"
```which will hopefully let you boot into a gui, though depending upon the card it may have slow graphics and no 3D capability or acceleration.
If you can get into the gui like this then at least you have your web browser on the macine in question.
Try installing the drivers in the repo again after purging all the packages with fglrx in the title, as above, but don't stop gdm or kill X or Xorg:
```
sudo apt-get remove --purge fglrx-amdcccle fglrx-kernel-source fglrx-modaliases xorg-driver-fglrx xorg-driver-fglrx-dev libamdxvba1
sudo rmmod fglrx
sudo apt-get install xorg-driver-fglrx fglrx-kernel-source
sudo aticonfig --initial

```then ctrl-alt-backspace to try it out.

---

### Post by 5oh on 2009-02-23
Thanks for the help, but alas it is a no go.

---

### Post by Bablefish on 2009-02-23
I hate to tell you this but it happens...A LOT!!! I have been on this forum for more than a year and I would swear it happens roughly 60% of the time, (based on all the posts that I have seen). It even happenend to me. Yes, there is a way to fix this. I was told how to, but my OS was NEVER the same. I hate to tell you this but there is only one way to fix this problem. Nuke your hard drive with a program called Dban. Then reinstall your OS.

---

### Post by zika on 2009-02-23
I want to disagree. first of all we are seeing here only the top of the iceberg since we are reading here (almost) only the scary stories of people that had problems. the majority is happily using the system (most of the time in blissful ignorance of possible problems).

the main feature of Ubuntu (or *nix generally) is its ability to be fixed without scars that are imminent in some other OS-s I do not want to mention in order not to start unneeded debates.

@5oh: You do not say what is the state of the system now. what happened with the recipe DagMan gave? I think that re-install is only the last resort and not even then ... ;)

also, take a look at the thread [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593) since I have a theory that all the tweaking with ATI drivers somehow stay logged and surface once when they I are least expected. there is a way of cleaning ... see there.

let us know if we could help in any way ...

---

### Post by DagMan on 2009-02-23
Yeah I agree.  Reinstalling is pretty drastic.

btw, I forgot that another way to get a basic gui back (we'd hope),is to either reboot after issuing the **apt-get remove** command above, and boot into recovery mode and selecting to fix the xserver, or to issue the apt-get remove command and then  **sudo dpkg-reconfigure -phigh xserver-xorg** so that's something else to try.
Ideally you can post the output of what the terminal says when you try to install the drivers and that would be a lot easier within a gui.

Also, do you have a custom kernel installed, or have you by chance used a program called kernel check?  You'de know right away if the answer was yes, so if you aren't sure then you'de be using the normal ubuntu kernel.  If you're using a custom kernel then a problem I had occur was with missing files from the kernel headers, and the solution was to recompile and just keep the source folder there rather than install the headers, and just install the kernel image.  I read somewhere on the forum of someone having troubles with a real time kernel as well.
If any of this applies, the best thing to try is to install the generic kernel and reboot into it, then install the drivers, and work from there.

Ideally, you'de be using the generic kernel, and you could post the output of apt-get when you try to install the driver.  It may also be a matter of removing paths to old automated module builds, so we haven't explored everything here yet even if none of the other stuff applies.

---

### Post by ssri on 2009-02-23
I had the same issue with ati's catalyst 9.1 installer.  It was a nightmare with respect to stability.  Primarily, I think my issue at the time was the fact that I neglected to purge ubuntu's old fglrx.  I learned my lesson since then.  Anyways, if you installed fglrx from ati's installer, you go into console and enter: 

cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh

purge ubuntu's packaged fglrx as seen from the instructions above
anjd type "sudo rm -r /etc/ati" just to be doubly sure

Then reinstall fglrx from repos (as stated in an earlier post in the thread).

Now back with 8.453 with the ol' video flicker problem.  Still, at least the system is stable.  fglrx 8.583? (catalyst 9.2) is pretty nice, but neither the power manager or "xset dpms force off" can turn off my laptop's monitor while idling, so it was a no sell for me.  Good luck!

--ssri

---

### Post by 5oh on 2009-03-03
I had to reinstall to get things working again. Well I shouldn't say I HAD to reinstall, but rather than waste anymore time trying to fix the problem, it seemed like a quick and easy way out.

I'm currently using the older version of catalyst and it works well enough for me to watch a movie. It sucks that I can't play any of the openGL stuff, but at least I can use the PC.

I'm trying REALLY trying hard to stay away from XP or Vista, but I'm not really liking the fact that I can't use my PC for more than 1 thing.

---

### Post by logicalinsanity on 2009-03-13
I just wanted to say that this post was insanely helpful to me in troubleshooting a similar issue.  I am brand new to Ubuntu (with no Linux experience whatsoever) and had screwed up my ATI drivers at some point trying to get s-video working on my laptop with a Mobility Radeon 9600.

My first attempt at using these troubleshooting steps failed for me, which [due to my frustration and inexperience] resulted in my completely reinstalling Ubuntu.  However, the display went wonky again after installing the proprietary ATI drivers on the clean stall (the problem ended up being their automatic installer) - but following these steps the 2nd time allowed me to reset everything.

In the end, I still used the driver from ATI's website - but instead of using their auto-installer, I did it manually following a guide posted on the Unofficial [ATI Linux Driver Wiki for Ubuntu 8.10]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

---

