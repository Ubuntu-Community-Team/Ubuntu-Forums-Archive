---
title: "Blank (not black) screen with cursor after login (related to 279833)"
date: 2006-11-01
forum: Desktop Environments
---

### Post by gregster on 2006-11-01
This is an extension of a reply I made to thread 279833, but as there was no resolution there for me I'm starting a new thread.

I know this seems the same as many other threads, but I have been unable to resolve the problem after having read them so...

Context:
Happy Dapper install for months. Then clean install of Edgy. No probs for weeks, then, after a restart I get the greeter, successfully log in, but get no splash (the one showing the various gnome components coming online). I do get a coloured background (ubuntu brown) but no desktop image. I get a standard cursor, but no panels, no right-click menu or anything else. Waiting for a long time does not help (I've left it for hours on more than one occasion). After a few minutes the screen goes black, but if I wiggle the mouse I get my brown background back.

Steps I took (not necessarily in this order):
* Looked through every log I could find. No issues were apparent.
* Stripped xorg.conf to the walls and then changed driver from nvidia to nv. Same result.
* Re-install gdm, gnome, metacity etc.
* Removed everything (hidden and otherwise) files/dirs from my home dir.
* Changed home dir location to another physical drive.
* Changed UID.
* Logged in as root and created new user(s). This was generally successful until a restart, then that user was no longer able to get a desktop.
* Installed KDE and XFCE. This worked fine, but I was unable to launch Gnome apps like nautilus. Launching from console gave no errors. I know I *could* use KDE or XFCE, but that isn't where I want to be.
* Gave up and reinstalled OS. Eventually had the same thing happen.
* Gave up and reinstalled Dapper. I am now at the same place I was with Edgy.
* Tried to boot LiveCD (Dapper 6.06, not 6.06.1). SAME THING!!!!

My machine (HW):
Tyan nForce4 mobo
Dual Opteron 250s
4GB RAM
1 400GB IDE drive
1 120GB SATA drive
2 160GB SATA drives
1 LG dual-layer DVD burner
1 Samsung 191T monitor
1 Samsung 204T monitor

My machine (pertinent SW):
686-smp kernel
Restricted modules installed, along with nvidia drivers from repos (not downloaded from nvidia).
nx server/client from nomachine
vmware workstation (latest release)

What's interesting is that if I log in through the nx client from my Mac I have no problems at all.

I'm not a complete dork, but I'm at my wits end with this. I can't even be sure it isn't hardware based, but the fact that my nx client and KDE seem to work fine leads me to believe that it's an OS/software/driver problem. I wasn't even sure which forum to post in.

I'm concerned that I will eventually have to switch to another OS if I can't resolve this ASAP. It's an important machine.

What logs/output should I post to support this thread?

Thanks a lot

---

### Post by RuarriS on 2006-11-01
do you have gnome session manager installed?

---

### Post by gregster on 2006-11-01
Yes I do. It's installed by default I believe.

---

### Post by gregster on 2006-11-10
No ideas anyone? Well, I've since re-installed the OS (back to Edgy) and ran fine for a week. I then installed a few apps and everything went kablooie.
Greet screen lets me log in, but I get a blank brown desktop with a cursor - nothing else. Eventually the screen goes black, but it will "wake up" when I wiggle the mouse. Occassionally I get a blank grey panel in the top left corner, but it doesn't contain anything (like text or buttons or borders).
The only non-repo app I've installed is VMWare workstation (latest release). I've since uninstalled it but I still have my problem. I don't notice anything on the VMWare forums, but I have noticed that when I ssh in to the machine and run "ps aux|grep gnome" I don't see too much going (no surprise I guess).
On the affected machine I see:
/usr/bin/gnome-keyring-daemon
/usr/lib/control-center/gnome-settings-daemon

Whereas on another machine I see the following processes
/usr/bin/gnome-keyring-daemon
/usr/lib/control-center/gnome-settings-daemon
gnome-panel --sm-client-id default1
/usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
gnome-power-manager
/usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=19
/usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=20


My current assessment is that for some reason, an app that I've installed (VMWare?) has hosed the automatic launching of gnom-panel and associated processes like gnome-applets et al. 

So my question is:
How can I set up my install so that it launches the required processes like gnome-panel when I log in?
Alternatively, if I ctrl+alt F1 to another tty, what command can I issue to launch gnome-panel etc. on screen 0 (not sure I worded that correctly, but I mean How do I launch gnome-panel etc. on my existing main screen.) I'm looking for something like "gnome-panel --display=0", but that doesn't work.

---

### Post by gregster on 2006-11-14
I may be having a conversation with myself, but at least this helps me record the problems.

I think this may be related to Bug#61381: 
[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381)
And I'm wondering if it may be connected to the fact that VMWare creates new network devices when it installs.

Further, I *think* that whatever is going on has *infected* the dapper codebase, as I get this same problem with Dapper installed.

---

### Post by gregster on 2006-11-15
I was able to reproduce this problem with a fresh install of edgy. I installed a few packages (java and nvidia drivers) from stock repos and shut the machine down, then restarted and got the behaviour. It seems to be when I actually shut the machine down (as in "shutdown -h") that it happens. If I "shutdown -r" it will be OK.

Is anyone out there?

---

### Post by ivanoats on 2006-11-15
I too am having this problem in Kubuntu. Any answers out there?

---

### Post by randal2k on 2006-11-17
I have same issue... there is only one option now that is happening in new release... drop Ubuntu for something else... going to try Suse.
I guess these linux guys are not so leet... so many people with this issue, and no fix.
It's a shame... This distro is nowhere near ready for use by anyone but people who program linux.. kinda blows there whole idea.


**UPDATE**
 Oh, and if you ask me ... it has soemthing to do with the NFORCE board and nothing to do with NVIDIA graphic drivers, also this is 100% related to bad configs or programming on UBUNTU's part... not the hardware, as SUSE works perfectly on my system... go figure!

---

### Post by risbac on 2006-12-13
I had more or less the same problem. 5 minutes to get the desktop, when it succeeds... But never at first log on, always after or remotly from another computer. The hosts file had a problem, I fixed it, but that's was not enough. I discovered it was ESD. So I have turned it off, and now my NXserver is working fine. I don't know if it's the same problem however, but that's worth a try maybe?

---

### Post by auburn on 2006-12-14
I seemed to have resolved my similar issue by editing my /etc/network/interfaces file. And I think bug 61381 (as noted by gregster) is related to my problem. I also suspect network-manager, which I believe I initially installed through automatix, was the cause of my problem.

---

### Post by gregster on 2007-03-28
I **think** I might have found a solution for me. After months of viewing all of the bug reports (and ignoring this one) I decided to give it a try.
Click on System>Preferences>Sound and set all "Device" prefs to ALSA. On the "Sounds" tab turn off "Enable software sound mixing (ESD)".
God only knows why this works, but it does. For me. I hope it works for you.

I have thought that it was an Ubuntu thing, but it apparently is a problem for Fedora (and other distro) users. It appears to be, at least in part, a Gnome thing.

A purely procedural issue for me was that I was unable to log in to any Gnome session in order to set the above prefs. I was unable to find a CLI solution either, so I ended up installing Fluxbox and logging in to a Fluxbox session, then:
start xterm
launch nautilus (which takes control of rendering your desktop)
launch gnome-panel
run through the Sound prefs as described above.
log out and launch a Gnome session.

This has worked through 3 reboots and two shutdown/restarts. If you were keeping track, my problem (in Dapper, Edgy and Feisty) was that I was fine until I shut the machine down (as in 'shutdown -h'). If I 'shutdown -r' I would normally be able to start a new session.

ps. I tried all the other things that worked for others, like the IPv6 changes, /etc/hosts etc. etc. They had no effect for me.

---

### Post by 2beers on 2007-05-19
Hi,

Same problem here - using feisty with gnome + KDE. Better said - KDE only as gnome doesnt work. (like described in this thread)

How can i do the described settings in KDE (for gnome)? What's the command to enter to start gnome's sound config?

---

### Post by dcherryholmes on 2007-05-27
Same problem here.  Fresh install on a Thinkpad A31 and my wireless isn't being seen, so adding fluxbox and going from there isn't an option here.  Maybe from work tomorrow I can get it straightened out.  Sucks.

---

### Post by FarmerDave on 2007-06-24
I just upgraded from dapper to edgy, and had this problem the first time I tried logging in.  Based on the tips given here, I was able to log all the way in by:

- Starting the login from the X login screen (enter username and password)
- Get stuck on the brown screen with just a cursor
- Switch over to a console by hitting CTRL+ALT+F1
- Login at the console prompt
- Find the esd processes: "ps wuax | grep /usr/bin/esd" 
- Kill the esd processes "kill process1 process2"
- Flip back to the X screen with CTRL+ALT+F7

And now I will upgrade from dapper to feisty. :P

---

### Post by FarmerDave on 2007-06-24
Oh, I should point out:  when killing the processes, don't just type "kill process1 process2" like I wrote here.  You should look for the numbers at the beginning of the lines produced by the "ps wuax", and kill those.  For example:

```
username     5734  0.0  0.1   1656   464 ?        Ss   21:59   0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 17
username     5735  0.0  0.3   3176  1504 ?        S    21:59   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 17
username     6375  0.0  0.1   2796   744 pts/0    R+   22:13   0:00 grep esd
```

In this case, you would "kill 5734 5735".  You don't need to worry about killing the grep process.

The downfall of ubiquitous linux will be that everyone assumes the users know what a process is. ;)

> **FarmerDave said:**
> I just upgraded from dapper to edgy, and had this problem the first time I tried logging in.  Based on the tips given here, I was able to log all the way in by:

- Starting the login from the X login screen (enter username and password)
- Get stuck on the brown screen with just a cursor
- Switch over to a console by hitting CTRL+ALT+F1
- Login at the console prompt
- Find the esd processes: "ps wuax | grep /usr/bin/esd" 
- Kill the esd processes "kill 5678 5679"
- Flip back to the X screen with CTRL+ALT+F7

And now I will upgrade from dapper to feisty. :P

---

