---
title: "Desktop with no monitor refuses to boot"
date: 2008-11-20
forum: Desktop Environments
---

### Post by Ralen on 2008-11-20
I have a spare computer I've installed ubuntu 8.10 on and planned to use it in conjunction with vnc rather than connect a monitor to it. It refuses to boot without a monitor, however, so I have to connect the monitor to it to boot. Is there any way to keep ubuntu from checking for a monitor when it boots?

**Edit: when I try to boot with no monitor, it stops during boot and displays the "Low Graphics Mode" screen until I reattach the monitor and continue the boot process

---

### Post by Ralen on 2008-11-21
Any suggestions would be appreciated. I'm totally new to linux, and my local contacts are not readily available.

---

### Post by Ralen on 2008-11-22
bump [11/22 21:00]

---

### Post by shcaesar on 2008-11-23
Here is my suggestion: google xorg.conf.
If I was right, you can disable X to check you monitor by doing some modifications to the file xorg.conf, which defines basic things of your monitor, screen and input devices.

---

### Post by Ralen on 2008-11-24
I found this page [[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)] but didn't find anything about skipping the monitor check. I've worked around the problem by running a cable to my tv, so technically it has a monitor now.

---

### Post by Coreigh on 2008-11-24
Do you need a graphical desktop or will this be a file/web server?

Do a google search for Ubuntu headless desktop or Ubuntu headless server

You could try disabling gdm, but again this will disable the graphical desktop.

---

### Post by Ralen on 2008-11-27
ya I do want the GUI intact so I can use vnc to connect

---

### Post by philly4 on 2009-01-02
Bump, cause I'm in the exact same boat.  I'd love to find some way for Ubuntu to skip the monitor check.  I just want to access the desktop remotely with my other computer.  Thanks to anyone for some help.

---

### Post by Jose Catre-Vandis on 2009-01-03
Most likely your motherboard requiring a monitor in order to boot. Check you bios settings for this.

Alternatively, do a command line install (press F4 at start up screen to install), or disable gdm / graphical interface, see here for info on how to do this:
[http://ubuntuforums.org/showpost.php?p=1010279&postcount=5](http://ubuntuforums.org/showpost.php?p=1010279&postcount=5)

---

### Post by apmcd47 on 2009-01-03
> **Ralen said:**
> ya I do want the GUI intact so I can use vnc to connect

> **philly4 said:**
> Bump, cause I'm in the exact same boat.  I'd love to find some way for Ubuntu to skip the monitor check.  I just want to access the desktop remotely with my other computer.  Thanks to anyone for some help.

Okay, this is a stupid question, but if you are using VNC to access the computer remotely, and will never use the GUI on the monitor, why do you need to run in graphical mode? The GUI will surely run in a pseudo-X Server started by VNC - this isn't Windows, you know!

My suggestion is to turn off Graphical Mode and see what happens then. The worst that can happen is that it still does not fully come up. At least you can then say that not having the monitor connected is not an X problem. If it does come up then you can experiment with logging in remotely and starting VNC.

Andrew

---

### Post by bartvh on 2009-01-03
TightVNC's server uses it's own virtual X display.

---

### Post by philly4 on 2009-01-03
First thanks for the help.  I really do appreciate it.

> **Jose Catre-Vandis said:**
> Most likely your motherboard requiring a monitor in order to boot. Check you bios settings for this.

Alternatively, do a command line install (press F4 at start up screen to install), or disable gdm / graphical interface, see here for info on how to do this:
[http://ubuntuforums.org/showpost.php?p=1010279&postcount=5](http://ubuntuforums.org/showpost.php?p=1010279&postcount=5)
I'm pretty sure it's not a bios thing.  The computer boots just fine to xubuntu, but then seems to "hang" in the process of loading the desktop.  When I plug a monitor in after booting without one, it says its running in low graphics mode and there is a dialog box that has an ok box to click.  When I click the ok, the desktop continues to load and everything works normally.  The problem for me is that some services that I want etc. don't load until after clicking on the ok dialogue box.  Everything works just fine if a monitor is connected at boot.

I'm interested in your suggestion to not load gdm.  I think it might do what I want.  However, could you please post how to turn it back on if I need it back before I try to turn it off and get stuck?  I'm new to linux and I'm not entirely comfortable without any gui available.  Thanks.

> **apmcd47 said:**
> Okay, this is a stupid question, but if you are using VNC to access the computer remotely, and will never use the GUI on the monitor, why do you need to run in graphical mode? The GUI will surely run in a pseudo-X Server started by VNC - this isn't Windows, you know!

My suggestion is to turn off Graphical Mode and see what happens then. The worst that can happen is that it still does not fully come up. At least you can then say that not having the monitor connected is not an X problem. If it does come up then you can experiment with logging in remotely and starting VNC.

Andrew
Somewhat answered above, but basically I'm new to linux and trying to set up a server, but it's much much easier for me to set thing up on that computer with a desktop and a monitor mouse and keyboard attached with a gui then after things are set up disconnect them.  After everything is set up, hopefully I wont need a gui at all.  Thanks again.

---

### Post by Jose Catre-Vandis on 2009-01-04
> However, could you please post how to turn it back on if I need it back before I try to turn it off and get stuck?

```
sudo /etc/init.d/gdm start
```

Assumes you are using gdm (default for gnome and xubuntu)

---

### Post by DefineByte on 2009-01-04
You need to recompile the kernel with the 'Enable firmware EDID' option disabled. Without this the boot sequence will hang for quite a while (15-30 minutes? I forget how long but if you leave it it should still boot eventually) without a monitor connected, or even without a VGA cable that supports DDC (some seem to omit the necessary wire, at least I know Belkin do/have done).

edit: Hmm, re-reading the first post it sounds like you get further than I thought so ignore. :D

---

### Post by philly4 on 2009-01-04
> **Jose Catre-Vandis said:**
> ```
sudo /etc/init.d/gdm start
```

Assumes you are using gdm (default for gnome and xubuntu)

Thanks.  Confirm this only starts gdm, but wont make the computer boot with gdm if I previously did: ```
update-rc.d -f gdm remove
```
How would I get the computer to boot with gdm?  This possibly?
```
update-rc.d -f gdm add
```

Edit:  I was playing with```
sudo /etc/init.d/gdm stop
```
After stopping gdm, I can't get gdm to start without rebooting.  After stopping GDM and typing```
 sudo /etc/init.d/gdm start
```nothing happens.  Nothing happens for any command I type.  I guess there's more to it.  There's no prompt like in terminal i.e. user@computer:~$.  Do I have to type all that in to do a command, or is there some way to bring up the prompt?  Thanks.

---

### Post by Jose Catre-Vandis on 2009-01-04
You probably need to be doing all this at a console, so before you type any commands
go to another console
```
CTRL+ALT+F1 through to F6
```


Here is the alter-ego command to get gdm automatically starting again
```
sudo update-rc.d gdm defaults 13 01
```

after you type
```
sudo /etc/init.d/gdm start
```
and enter your password, you will probably just get returned to a prompt. To get the gui going again you may need to login and type 
```
startx
```

---

### Post by philly4 on 2009-01-04
> **bartvh said:**
> TightVNC's server uses it's own virtual X display.

As soon as I stop gdm, I can no longer log in remotely to my xubuntu system with the tightVNC viewer that I'm using on my other (windows) computer.  I'm running vino as the VNC server on xubuntu and it works great as long as gdm is running.  Is there a different thing to type into the login without at desktop running?

---

### Post by syborfical on 2009-01-05
> **Ralen said:**
> I have a spare computer I've installed ubuntu 8.10 on and planned to use it in conjunction with vnc rather than connect a monitor to it. It refuses to boot without a monitor, however, so I have to connect the monitor to it to boot. Is there any way to keep ubuntu from checking for a monitor when it boots?

**Edit: when I try to boot with no monitor, it stops during boot and displays the "Low Graphics Mode" screen until I reattach the monitor and continue the boot process

Yes there is first thing you need to do is uninstall there default VNC server. Do no use remote desktop the crap that comes with ubuntu.

You need to change you xorg.conf
and change a few things in you gdm.conf

I'm in the middle of setting this up myself.

I have my ubuntu 7.10 file / dev box set up this way.
It has a power cable and network calbe installed.
SSH and VNC start up when the machine starts. 

And yes you can do it...

---

### Post by Jose Catre-Vandis on 2009-01-05
> **philly4 said:**
> As soon as I stop gdm, I can no longer log in remotely to my xubuntu system with the tightVNC viewer that I'm using on my other (windows) computer.  I'm running vino as the VNC server on xubuntu and it works great as long as gdm is running.  Is there a different thing to type into the login without at desktop running?

Right, I wasn't sure if you were working at the ubuntu PC with the monitor attached to get it working or not :)

To get remote access without a gui you need ssh.

```
sudo apt-get install openssh-server
``` (might already be up and running). Next, download putty.exe to your windows machine:
```
http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe
```
Run putty.exe (no installation required) and enter your remote machines IP, username and password, click Connect, and you should get a dosbox open with your command line login. You may be queried about ssh keys, just say yes to connect. Now you can run the commands above remotely.

---

### Post by nkhong on 2009-01-29
Ok after a thorough research, I have finally figured out how to correctly do this for ubuntu 8.10 desktop.

My goal a "headless gui-driven ubuntu" server to serve as both a home file server and a development server.

I started out with Ubuntu Desktop 8.10.  The xorg.conf auto magically detects everything so that has be redone so that it doesnt try to detect your monitor even when its not there.  These are the steps to change the /etc/X11/xorg.conf file so that Ubuntu desktop will log in without your monitor and input devices.

1) Relogin into recovery mode (press 'esc' at grub) startup
2) Enter root shell from the recovery options
3) run Xorg -configure
4) test the newly generated config: Xorg -config xorg.conf.new
5) backup the original /etc/X11/xorg.conf to another location
6) copy the new xorg.conf.new to /etc/X11/xorg.conf

Further more if you want a remote X login.. you have 2 options
1) straight from XDMCP using Xming. To enable System->Administration->Login Window->Remote tab->Same as Local. To download Xming go here: [http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

2) second option is to use vnc gdm login prompt... instructions here will work for 8.10 also: 
[http://ubuntuforums.org/showthread.php?p=5229232#post5229232](http://ubuntuforums.org/showthread.php?p=5229232#post5229232)

Good luck,
-Rakon

---

### Post by airzoink on 2009-02-01
> **nkhong said:**
> Ok after a thorough research, I have finally figured out how to correctly do this for ubuntu 8.10 desktop.

My goal a "headless gui-driven ubuntu" server to serve as both a home file server and a development server.

I started out with Ubuntu Desktop 8.10.  The xorg.conf auto magically detects everything so that has be redone so that it doesnt try to detect your monitor even when its not there.  These are the steps to change the /etc/X11/xorg.conf file so that Ubuntu desktop will log in without your monitor and input devices.

1) Relogin into recovery mode (press 'esc' at grub) startup
2) Enter root shell from the recovery options
3) run Xorg -configure
4) test the newly generated config: Xorg -config xorg.conf.new
5) backup the original /etc/X11/xorg.conf to another location
6) copy the new xorg.conf.new to /etc/X11/xorg.conf

Further more if you want a remote X login.. you have 2 options
1) straight from XDMCP using Xming. To enable System->Administration->Login Window->Remote tab->Same as Local. To download Xming go here: [http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

2) second option is to use vnc gdm login prompt... instructions here will work for 8.10 also: 
[http://ubuntuforums.org/showthread.php?p=5229232#post5229232](http://ubuntuforums.org/showthread.php?p=5229232#post5229232)

Good luck,
-Rakon
hello there! I tried your procedure and it does not seem to work. Do you have a more detailed guide? Maybe i missed a step. Would really like to make my system run headless. Thanks!

---

### Post by mister_p_1998 on 2009-02-02
I had a problem with Intrepid failing to but because I had two network cards in the machine, one was connected and one wasnt, it sat there looking for a connection on the unused one and  didnt seem to time out, pulled the card out and all was well. I wonder if its doing the same thing looking for a  monitor?

Steve

---

### Post by airzoink on 2009-02-02
> **mister_p_1998 said:**
> I had a problem with Intrepid failing to but because I had two network cards in the machine, one was connected and one wasnt, it sat there looking for a connection on the unused one and  didnt seem to time out, pulled the card out and all was well. I wonder if its doing the same thing looking for a  monitor?

Steve
I bet it is monitor detection. The thing is I only have one video card installed and it is integrated (intel) with the motherboard. Same issue as described in this thread. When I disconnect the monitor i get the error. When i connect it, it boots up normally. Help! Would like to run it headless.

---

### Post by airzoink on 2009-02-12
Found a solution! I made a VGA terminator. Here is a link on how to make one. 

[http://www.mp3car.com/vbulletin/general-hardware-discussion/1763-how-does-video-card-detect-vga-monitor-present.html](http://www.mp3car.com/vbulletin/general-hardware-discussion/1763-how-does-video-card-detect-vga-monitor-present.html)

I just tried it today and it worked like charm. Got parts from a broken monitor lying around.

---

### Post by hutchia on 2009-03-25
I had a similar problem with Debian and it took a long while to figure out the simple fix.

Boot would stall when no monitor was found.

Here is why and how to fix:

The Video drivers now auto-detect monitor, and in particular its available modes. It will only do this with monitor connected. I spend long time looking for work around here - but this was wasted time.

Xorg software stalls during boot when it gets video error because it prompts user to look at log file and/or continue. There are some scripts that get invoked when error occurs. I was very tempted to rewrite these so they did not require for keyboard input on error.

Then it came to me! 

The Xorg software was set up to create XSERVER on console (ie normal monitor/keyboard) - expecting this to be used as Xterminal to access applications locally or elsewhere.

Though I am using an XServer, it's not local. In my case I was running GNOME desktop so a check on the login setup (login window prefs, security,configure x-server) shows VT0 listed as Xserver. Removing this entry FIXED THE PROBLEM!

An Xserver can still be run on machine after connecting monitor - just log in and type startx.

---

### Post by speaktek on 2009-04-23
Get a 15-pin male connector from Radio Shack: 276-1501
Get 3 resistors: 271-1106 (5 pack / 68 ohm...works fine)
Solder resistors between pins:
1-6
2-7
3-8

Plug in...boot up...life is good!

Should work for most mother boards...

;-)

---

### Post by cmfarley19 on 2009-05-12
hutchia,
I have been struggling with this since I upgraded from Hardy to Jaunty.
I posted about it a few weeks ago:
[http://ubuntuforums.org/showthread.php?t=1143015](http://ubuntuforums.org/showthread.php?t=1143015)

If I were to do this (removing VT0), will I still be able to VNC into this system and get presented with a GUI?

I recall something from a long time ago that you could put something in a ~/.ssh or ~/.vnc file that will launch a script to start the GUI when you try to login in VIA SSH or VNC.

Does any of this sound familiar?

Chris

---

