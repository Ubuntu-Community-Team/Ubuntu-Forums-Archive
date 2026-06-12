---
title: "X: user not authorized to run the X server, aborting."
date: 2007-11-27
forum: Desktop Environments
---

### Post by theDaveTheRave on 2007-11-27
Hi all.

Well an interesting problem.

I'm running Fiesty by the way.

I was playing with setting up VNC server and stuff (to log onto my server box at home - which curently doesn't have a VDU!).

Anyway I finished up (not quite got it working yet), and did a update through the update manager finished for the day.

Today I got home form work and start up my laptop... everything seems fine, but then I don't get a log in screen!

I reboot into safe mode and <login davem> to get into my home area. I then do a <startx>

this gives me the follwing error
> 
davem@Planchet:~$ startx
xauth:  creating new authority file /home/davem/.serverauth.4809
X: user not authorized to run the X server, aborting.
xinit:  Server error.


I then searched all around the Ubuntu forums and couldn't find anything to help.

Then whilst adding in this new thread I find a thread, it advised to do this

> sudo dpkg-reconfigure x11-common

suggesting to have "anyone" to start the xserver. this seems OK but there are some security issues... can anyone advise please??

Anyway, after this I did a reboot, and still didn't have access to the login screen? so back again through the safe mode.

from the root area I loged into my personal area and did a <startx>

this threw up a couple of errors as follows.
> 
Can't access ACPI events in /var/run/acpid.socket! Make sure the ACPI subsystem is working and the acpid daemon is running.

and
> 
Internal error

failed to initialize HAL!


Another thread I found said to check the output of  < ls -l .Xauthority .ICEauthority> which was
> 
-rw------- 1 davem davem 163 Nov 27 23:43 .ICEauthority
-rw------- 1 davem davem 102 Nov 27 23:04 .Xauthority


which is how it apparently should be!

so why do I still have a problem with not getting the startup login screen?

I'm sure I'm forgetting something... I did mention I'm using Fiesty, and did an update via the update manager?

hope you have enough informaion in all of this to help me out.

Thanks a billion in advance

Dave

---

### Post by theDaveTheRave on 2007-11-28
Hello again.

Obviously a fair number of people have had a look at my problem and it must have you all scratching your heads! 

so I've got a temporary solution.

run the command 
> 
sudo update-rc.d -f gdm remove


to remove gdm from the startup procedure, and no more startup splash screen.

edit the x11 conifg (see my first post), and allow "anyone" to run the x11 server.

so now I boot into the terminal, login in as my name and password, run startx and "yipee kye eh" I have a desktop just like I like it!

now I guess I just need to understand what was wrong with the system earlier?

are there any log files I can drop into the thread that will help out??

Thanks all.

Dave

---

### Post by AndrewSharpe on 2007-11-28
Hi,

I'm not sure if it'll solve the problem of GDM not starting up at boot, but editing /etc/X11/Xwrapper.config and setting
> allowed_users=anybody
allows me to start a new X server from within an xterm (same as `dpkg-reconfigure x11-common`.  See `man Xwrapper.config`).  Before the edit I was getting
> X: user not authorized to run the X server, aborting.

---

### Post by theDaveTheRave on 2007-11-29
Andrew.

thanks for the suggestion. I assume however that reconfiguring the xconfig, as I have, to "anybody" is essentially the same thing? but I will check the file, as I suspect I will be able to simply put my username into the line!? - I'll try it an see.

The other thought that occured to me was that the login screen isn't actually opening in the first instance, and so may not be specific to any  login - so it occurs to me that maybe the permisions are generally wrong?

I can't seem to find any others with a similar problem on Fiesty, but there is an issue that seems similar to this from one of the Gutsy updates. But there are enough differences for me to feel that this is in fact a different problem somehow related to my "buggering about" trying to VNC to function in communication with my server!

If I could roll back to a known point in time where the system was previously working I would be able to backdate to last weekend (ie. 22nd Novemer) but I can't find instruction on how to do this either!

I guess I may have to simply do an update to Gutsy, but I have no guarantees that this will resolve the problem!

then of course I can't find how to save my emails so as i can reload them into evolution - or I would do a fiesty re-install / upgrade to Gutsy.

anyway I'm going to try not to think about whilst I am at work!

Dave

---

### Post by AndrewSharpe on 2007-11-29
Hi Dave, 

Yes I believe that my edit to /etc/X11/Xwrapper.config is the same as what you've done by `dpkg-reconfigure x11-common`, but I believe you cannot just put your username in that file (run `man Xwrapper.config`).

I'm not sure what you mean by > "buggering about" trying to VNC to function in communication with my server! but at a guess I'd say you were trying to incorporate it into your GDM config?

I'm using Feisty as well and after reading the comments at the top of /etc/gdm/gdm.conf and assuming you have changed the GDM config file(s) I'd suggest you uninstall GDM, remove any old config files then reinstall GDM, effectively replacing the original config files (maybe easier to do a forced reinstall?).  Then try what you want to do again, but this time only modify /etc/gdm/gdm.conf-custom and keep a copy of the original ;)

Sorry I can't be more help, debian/ubuntu is rather new to me.

Andrew

---

### Post by Peter09 on 2007-11-30
I have this problem as well, do not know what caused it. I am booting through recovery mode at the moment. I amended my x server so that I can do a startx from the terminal and can access my account by logging in from the recovery prompt as myself.

I am getting a HAL failed to initialise failure and cannot (through Users and Groups) edit my user and passwords file. It comes up with "failed to load configuration". 

Something seems to have screwed permissions, but I do not know how to recover from it.

---

### Post by theDaveTheRave on 2007-11-30
Andrew.

My comment of "buggering about with Vnc" was just for information, as I didn't explicitly play with any GDM config - - just thought it may be helpful info!?

Peter.

try doing the trick suggested by Andrew and then removing the graphical logon screen. then you get a simple logon prompt and can start gnome / kde with a <startx> command.

I'll work through the solutions and post once I have solved.

speak later.

Dave

---

### Post by AndrewSharpe on 2007-11-30
For the permissions problem running "Users and Groups", you must be in the admin group to use that (or in the sudoers file somewhere, see `man sudoers`).  You can check by logging in as yourself, then running `groups`.  Here's what I've got for myself
```
andrew@ase:~$ groups
andrew adm dialout cdrom floppy audio dip video plugdev games scanner netdev lpadmin powerdev admin

```
It may be that you've been removed from the admin group for some reason, but I don't think that accounts for the start X at boot problem.

---

### Post by Peter09 on 2007-11-30
Here is the output of my groups command, from my untrained eye it looks ok.

peter@mesh:~$ groups
peter adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin

---

### Post by AndrewSharpe on 2007-11-30
OK, now you can run `sudo -l` to see what you're allowed to run as root.  It might also be useful to show the contents of /etc/sudoers (you'll need to be root to read that file).

---

### Post by Peter09 on 2007-11-30
Hi,
I have just implemented the change to allow a straight text login, rather than going through recovery mode and then logging in as myself and then starting x.

The problems with HAL failing to initialise and being unable to edit "User" has disappeared. 

It appears that these two problems were symptoms of recovery mode login :( . I wonder whether this is a common thing across other peoples systems.

So - now I am in the same position as Dave, cannot login using the normal screen.

Thanks for you help in this, I have been struggling for a long time to resolve this.

---

### Post by AndrewSharpe on 2007-11-30
No prob.

Let's try and get some info on why GDM won't work for you.  First, make sure X is stopped.  So you should be at a console (ctrl + alt + F1) and there should be nothing at ctrl + alt + F7.  Then try starting GDM as root - `/etc/init.d/gdm start`.  Then post any error messages you see and the contents of /var/log/gdm/:0.log.  We'll have a look at that and see if there's anything useful.

---

### Post by Peter09 on 2007-11-30
Unfortunately I have a Logitech keyboard with programmable function keys, they are not working at the moment, so I rebooted and issued the command from the text  prompt after I logged in.

I immediately see the login screen flash up for half a second or less and the straight to a blank screen from which I cannot recover, needed to reboot.

---

### Post by AndrewSharpe on 2007-11-30
Sorry, I didn't think.  You don't need to restart X to get that log file (/var/log/gdm/:0.log) and you can just post it now, hopefully it will be really helpful.

As for the hanging X, for future reference you may be able to get back to a console with ctrl + alt + backspace.  GDM usually tries to start X a number of times before giving up so you may need to go through that procedure a few times.

---

### Post by Peter09 on 2007-11-30
Control-Alt-Backspace does not work.

Here is the contents of the file:

[ATTACH]51841[/ATTACH]

---

### Post by AndrewSharpe on 2007-11-30
This line > (EE) fglrx(0): Failed to enable interrupts. appears to be the best lead, but I'm fairly sure that's not the problem because X starts fine from startx, and the log doesn't indicate that X has died so it looks like the problem might be with the actual GDM start screen.

Thanks for providing the info, but I think this one is beyond my powers, sorry.

---

### Post by Peter09 on 2007-11-30
Thanks for the effort Andrew

---

### Post by theDaveTheRave on 2007-12-05
Hello All.

Well I haven't had a lot of time to properly investigate / try to resolve this issue at the moment, due to commitments of trying to get some software working that I am writing!

Once I have this working I will do a "reinstall" of Gnome (remove and then a re-install) as suggested by Andrew.

Peter.

Are you still unable to use Gnome / KDE ?? are you logging in through the graphical screen or via a text logon?

My solution of doing this seems to work just fine, although to shutdown I need to do a >  shutdown -h -0  and put in my root password (eg doing it a sudo!).

Otherwise it seems like a nice solution.... I may make it look even more geeky and turn on verbose mode and loose the little Ubuntu splash screen and process bar :)

anwyay I'm going to try to get time to work on this more over the weekend..... I hope!

Dave

---

### Post by Peter09 on 2007-12-08
Still just logging in through text mode and then running startx.Once in everything seems ok, as normal. 

I have not tried logging in through the graphical interface, I turned it off using a terminal command and now not sure how to turn it on again :) although I have not made much effort in this respect.

As said before, I'm not sure where to go from here, I have an operational desktop, just a little clunky at startup.

---

### Post by theDaveTheRave on 2007-12-09
Hi all.

I found another user with a related problem, in that the error message is similar to one that I get when I boot up, with a note about there being no restart image?

the thread is here

[http://ubuntuforums.org/showthread.php?t=634555]("http://ubuntuforums.org/showthread.php?t=634555")

He is simply going to re-install, which is what I will do eventually. once I have finished one of my projects that I am working on.

Dave

---

### Post by Peter09 on 2007-12-10
Hey, I get the same messages as these as well:-
=============================
Code:
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/(UUID number)) = hda5(3,5)
kinit: trying to resume from /dev/disk/by-uuid/(UUID number)
kinit: No resume image, doing normal boot...

Ubuntu 7.10 mike-desktop tty1

mike-desktop login:
===============================

I assumed that they were not error messages but just the system checking to see if there was  a hibernation image. It is interesting because I remember at one stage testing my Desktop to see if it could sleep or hibernate. It failed both times and appeared to hang. I cannot recollect if the timescales are connected to the machines failure to graphically boot.

---

### Post by theDaveTheRave on 2008-02-02
Hello Again All.

Well I have had a little while off whilst doing other stuff.

Briefly I have had some other issues also, the sound seems to have stopped functioning - I returded the unit (an ACER Aspire 3680) to the manufacturer, and they insisted that it was a software error - which I didn't accept. so they sent it back without any sound solutions!

When I received it back I was able to get my files by using a the live Fiesty CD. Then simply re-installed the system.

Everything is working again now, but I can't get sound from the speakers - I have tried the same methods as previously bu still nothing - so now I am thinking that there really was a problem with the sound card / speakers, and Acer where just trying to get around the issue by saying that it was an Ubuntu issue. I am yet to try the headphone jack to see if I can still get sound that way? but personally I'm not too bothered.... I do miss the BBC listen again function though!

Post install and everything is working agian - apart from sound obviously! I am wondering if the sound issue was in fact the real problem?? I saved all the system log files and everything, but don't know what I am looking for, if anyone has any ideas then I'll happily drop a copy of the relevant lines into the forum.

Otherwise I hope that other with this issue have been able to find satisfactory solutions.

Dave

---

