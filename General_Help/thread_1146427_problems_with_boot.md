---
title: "problems with boot"
date: 2009-05-02
forum: General Help
---

### Post by melodicmetal on 2009-05-02
I am very new to ubuntu and do not know how to use linux commands yet. I have upgraded ubuntu to 9.04 from intrepid since I have really enjoyed ubuntu so far. Now when I start my comp, it freezes before loading the login window. I see only a blank screen. 

I am using a Dell Optiplex 170L with 
Pentium 4 2.80Ghz
1.00 GB of RAM
80GB Hard Drive

I have no other OS installed on it and I already reinstalled Ubuntu hoping it would fix it so there is absolutely nothing on the computer except what comes with the install.

I can start up if I go into recovery mode. I really have no clue where to begin and I am trying to read what I can to learn how to use commands. Could someone please help me to fix this problem with beginners instructions. I do not have time or money to go and read a book about linux, though I plan to do so soon. I would like to know if there is an easy fix for this or do I give up on linux until I learn more about it?

---

### Post by 3Miro on 2009-05-02
Sounds like a video problem. What exactly is your video card?

You can go to the terminal (Apps -> Accessories -> Terminal) type:
```

sudo lshw

```

That will show all of your hardware.

Go to System -> Admin -> Hardware Manager and see if there are any drivers available (or did you already do that).

---

### Post by melodicmetal on 2009-05-02
I have the original intel 82865G graphics card, I checked for drivers, I do not believe there was one available. I am using a new 19" monitor and it looks great, the appearance doesn't seem to suffer at all and it is working when I boot in recovery mode. 

In the terminal * -pci it says this: 

configuration: driver=apgart - intel module=intel_agp
*display UNCLAIMED

does this help to identify anything

---

### Post by 3Miro on 2009-05-02
Go in recovery mode and try those two commands:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_mybackup
sudo dpkg-reconfigure xserver-xorg

```

The first one makes a backup file for the display configuration and the second one reconfigures the display. Reboot and hopefully it will work.

---

### Post by codeseer on 2009-05-02
There are a lot of problems occuring with Jaunty. You should have really stuck with 8.10 until some of them are fully straightened out. Hopefully you used Ext3 instead of Ext4. What you probably need is a Kernel upgrade and a shifting of the Intel configuration.

You can do the upgrades by following this guide:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

You can use nano where it says gedit and sudo where it says gksudo most likely; but if you're in recovery, the sudo part probably won't be an issue.

However, if you're happy with 8.10, I would consider going back to that for right now. 9.04 doesn't have a lot of new additions; not much that you can't get on 8.10 anyway.

---

### Post by delcypher on 2009-05-02
@3Miro - melodicmetal can't boot into X, so how is he/she supposed to use Hardware Manager.

Looking up your computer it says your Graphics setup is "Embedded Intel Extreme®  Graphics 2". I don't know much about getting intel graphics working on Ubuntu, although I've heard people have been having [problems (there's a guide here you could try)]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").

At the recovery menu the first thing to try is the "fix X" option and then try and continue to boot.

You could try switching to the VESA driver (explained below), which is the really basic video driver (it won't look so good, or be very fast but at least you can get something working for the moment).

A few command-line tips:
1.[TAB] is auto complete, you can use this complete filenames and program names (e.g. if I type to  then press [TAB] twice I will get a list of possible options. It's pressed twice because there is more than one option, if there is one then when you press [TAB] the first time it will complete what you've started typing for you).

2. If you want to read up on a command type ```
man program_name
```. This will bring up the manual for that program. Press q to quit and h, for help on navigating.

3. If you to search for a command based on its description type ```
man -k search_term
```

Okay here are a few things to try.

In the recovery mode drop to the root shell prompt and type

```
dpkg-reconfigure -phigh xserver-xorg
```

then type exit, then select "resume booting" (it might not be called that exactly)

- I took that from ```
http://ubuntuforums.org/showthread.php?t=719473
```

you could try this too (will probably do the same thing)

```
nano /etc/X11/xorg.conf
```

now scroll down and find the   Section "Device"    part and change
```
Driver      "[your_driver_name]"
``` to
```
Driver      "vesa"
```

then press [CTRL]+x then press Y. You should of now left the nano editor and should be looking at the command prompt again. Type exit and choose the option to resume booting.

Like codeseer said it might be worth using 8.10 instead. It is available [here]("http://releases.ubuntu.com/8.10/")

Hope this helps.

---

### Post by melodicmetal on 2009-05-02
3Miro,

Thank you very much, that seemed to work and I restarted with no problem. I appreciate the help. Could you tell me what that did? Was it a problem with the video card configuration?

Thank you, you must definitely know a lot about IT since you were able to help me so quickly. If it works from now on than I will know it was a simple fix. I will keep all the other information as a reference and hopefully this will help others as well!

I only used the 2 commands, 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_mybackup
sudo dpkg-reconfigure xserver-xorg

---

### Post by 3Miro on 2009-05-02
The problem was with the video configuration. The configuration is in /etc/X11/xorg.conf file. What you did was, first made a backup of the file (now there is a file called /etc/X11/xorg.conf_mybackup that contains your broken configuration). Second you make Ubuntu reconfigure the video setings (sudo means Super User DO, that is assume administrative privileges, dpkg is the package manager and xserver is the backbone program responsible for all video stuff).

BTW is recovery mode a command line only? I thought it had some basic graphical stuff.

---

### Post by gospel100 on 2009-05-08
I don't know if quick reply is the right thing to do here.  I have a similar problem.  I just installed the Ultimate Edition 2.1 with ubuntu 8.1.  the live cd works great.  the install went flawless, but when i was instructed to reboot, I did and x crashes on bootup.  Saying something about no modual, no nvidia driver.  i reinstalled the live cd and went to hardware to see about proprietary drivers.  it said there were no proprietary drivers in use.  so, I downloaded and installed the nvidia ver. 177 (which was recomended by ubuntu) and restarted x.  Things went great until I rebooted.  Same prob.  X crashes.  How do i get the settings I downloaded and installed to stay there?
Chris

---

