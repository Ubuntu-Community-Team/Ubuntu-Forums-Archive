---
title: "starting without a monitor / disable monitor detection on startup"
date: 2007-11-21
forum: Desktop Environments
---

### Post by netbuz10101 on 2007-11-21
Im trying to set up multiple computers on a network without monitors attached. Im using vnc to access them when not maintaining them.

I need the computers to start up without bringing up the dialog about low graphics mode, and to just use the configuration i set. (1024x768@75)

I dont know why, but one computer will do this fine, but the one in question wont. I tried commenting out all the resolutions in the xorg.conf file, but that doesnt change the way it starts up. After i attach a monitor, and try to configure the resolution monitor, it will ignore those changes.

!! now it wont detect the monitor even if its attached during startup!!

Im going to reinstall ubuntu 7.10 fresh, but this is not the first time ive done this

Any ideas on how to get those objectives?

Startup with normal settings regardless of whether a monitor is attached or not


thanks!

---

### Post by Levander on 2007-11-21
You need to learn a little about jumpstart and runlevels.  By default, Ubuntu boots into runlevel 2.  Change the init.d scripts so that X is not started in runlevel 2.

---

### Post by netbuz10101 on 2007-11-21
Can you explain a little more? I checked the init.d folder and it looks like a bunch of scripts/programs that it runs upon startup. there was a script called screen, it said it would refresh graphics pipelines or something, but getting rid of that didnt do anything so i went ahead and threw a new install on. Could you point me in the right direction? I also tried looking up jumpstart on the web and couldnt find anything. More help would be greatly appreciated!

thanks

---

### Post by Levander on 2007-11-21
The script you want to disable will be called S??gdm in the /etc/rc2.d directory.  It's a link to /etc/init.d/gdm.  S in S??gdm is for start, it starts gdm when you enter the runlevel.  You want to name it K??gdm so that gdm is killed, if its running, when you 

But, I don't think just changing the script names directly on the filesystem is the "approved" way of doing it.

I got it wrong, it's called upstart, not jumpstart.  I just looked around for a few minutes and couldn't find any good doc.'s.  Sorry.

If you find an "approved" way of changing what scripts get started and stopped in each runlevel, please post it in this thread.  I'd like to know what it is.

---

### Post by netbuz10101 on 2007-11-22
Wont that make it not start gnome?

I need it to start like it would normally do with a screen attached, but regardless of whether a monitor is really there. it wont proceed to displaying the desktop because it throws up a dialog that says :
UBUNTU IS RUNNING IN LOW-GRAPHICS MODE your screen and graphics card could not be detected correctly. etc...

How can i disable this detection on startup and just use settings i tell it every time?

so far i spent at least 20 hours just playing around with things and trying to figure out what to do to make it start up smoothly. -wish i knew more *sigh*


If i could get it to work like i want on my machines, i was going to show this to a friend to save him money on a renderfarm for cg work. It needs to work as headless computers with GUIs accesable via VNC as they cant spend time in an unfamiliar text based enviroment. this issue really puts a kink in the whole process.

---

### Post by Levander on 2007-11-23
I'm not sure how to do this.  

I know that dialog that pops up saying "Low Graphics" is called Bulletproof X.  If X doesn't start with your regular configuration (in xorg.conf) it falls back to a "failsafe" aka "bulletproof" configuration in xorg.conf.failsafe.  When it falls back to that very simplified configuration in xorg.conf.failsaife, you get that dialog.  

I don't know, I assume you can disable bulletproof X, but then you won't have X running at all...

That sounds like the wrong direction though.  You want X running without a monitor attached.  What that "low graphics" dialog means is that X isn't running.  And, it's asking permission to restart X in low graphics aka bulletproof aka failsafe mode.

I think what you're talking about is typically done in X with XDMCP.  you can run all the applications on a server, and they just send graphics commands to all the workstations.  The workstations read these graphics command and send these commands to their graphics cards, and they're displayed.

When you run vnc, I don't think X even realize vnc is running.  vnc just captures whatever X spits out on the screen.  But, X just thinks it's spitting it out on the screen.  That vnc is capturing it, has nothing to do with X.  Maybe though, there's a way so that X thinks it has a screen it's spitting stuff out on, even though their's no physical monitor.  Then, I guess vnc could catch whatever X spits stuff out on.

Basically, It's not that you need to get rid of that "Low Graphics" dialog.  It's that you need to figure out how to get X to run without a monitor, to do it your way with VNC.

But, I believe what you're trying to do is typically done with XDMCP.  If your "friend" doesn't know about XDMCP, he has no business running a server farm.  I'd suggest to him working for someone else who has a server farm, then after he has some experience, then he can invest in his own.

20 hours figuring out how to do something that's infrastructure for a network like you're doing is nothing.   Learning takes time.  The more you've learned, the easier it gets to learn.

It probably does make it more frustrating that you may even be going in the wrong direction.  

I"ve never done what you're trying to do.  I'm just telling you what I know about it.

---

### Post by grizn0 on 2007-12-14
Has there been any headway made on this? I'm having the exact same issue...

---

### Post by netbuz10101 on 2008-01-08
Still have this issue. I forgot to mention the reason i really want to use VNC is that my work stations are windows (mixed pro and home) so VNC works for every platform. Anybody know what needs to be done to make this work?


thanks

---

### Post by mmadd29 on 2008-01-18
I just did what you wanted.  I'm doing the same thing and running VNC on a Windows laptop to control my Ubuntu machine which is my firewall/ VPN server/ Internet filter.

Here is what I did:

I rebooted without the monitor, plugged in the monitor and got the low graphics screen.

I rebooted with the monitor and logged into the machine.

At the terminal I did:

sudo dpkg-reconfigure xserver-xorg

At the screens it asked to auto detect the monitor, keyboard, and mouse.  I said NO at each prompt.  Now it did detect everything, but at the end when I told it to write the values to xorg.conf, it wrote them to not detect anything.

I did: shutdown -r now

I unplugged the monitor before it shutdown.

After restart I waited 5 minutes and plugged in the monitor, at it was sitting at the login screen.  I logged in and was good to go....

Now I just need to figure out how to get tightvncserver to load at boot, not after I login.

---

### Post by naich on 2008-01-22
Bah, I'm having exactly the same problem but the dpkg-reconfigure with no autodetecting didn't fix it - I'm still getting the "Low graphics mode" stupidity.

The reason I'm doing it with VNC is because xdmcp doesn't work.  Looks like I can't win :(

---

### Post by glaurens on 2008-01-24
Found the solution:

just add the line

Option "ConnectedMonitor" "CRT,CRT"


under the relative device section. Obviously if you are only running one monitor per GPU then use only one CRT.

Now I'm off to go and play with the different modes since it boots up with the incorrect resolution now, but at least it works.

The link where I found this is:

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Connecting_a_second_monitor_after_X_startup](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Connecting_a_second_monitor_after_X_startup)

G

---

### Post by naich on 2008-01-24
> **glaurens said:**
> Found the solution:

just add the line

Option "ConnectedMonitor" "CRT,CRT"


Nope, it still won't start headless in anything other than low resolution mode.  I tried that line in every section of the file and even made it's own section.  

The video is onboard an Intel D845GLVA M/B - it's an 82845 chipset.  Maybe it's worth trying a different video card?

---

### Post by naich on 2008-02-01
I think I've got it cracked,  I deleted ALL files beginning with xorg.conf* (probably including the fallback one by mistake) in /etc/X11 and did a dpkg-reconfigure -plow xserver-xorg making sure nothing was auto-configured.  Then I removed all the screen resolutions except 1024x768 from the new xorg.conf and it now seems to boot into X OK when it's headless.  I've no idea which one of those things did the trick.

---

