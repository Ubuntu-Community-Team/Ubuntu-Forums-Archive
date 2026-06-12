---
title: "Can't open Firefox over ssh on Ubuntu systems"
date: 2023-06-15
forum: Desktop Environments
---

### Post by bjrosen on 2023-06-15
X forwarding isn't working for Firefox, it's fine for everything else. When I try and start Firefox I get

(process:82629): dconf-CRITICAL **: 19:35:23.382: unable to create file '/run/user/500/dconf/user': Permission denied.  dconf will not work properly.
X11 connection rejected because of wrong authentication.
Error: cannot open display: localhost:11.0

This error is specific to systems that are running Ubuntu 22.04, I have no problem when the remote system is CentOS 7 or if I start any application other than Firefox.

---

### Post by TheFu on 2023-06-16
It is due to snap confinement on the remote system.

The workaround is to remove the snap version of firefox and load a non-snap version, perhaps the ESR from the Mozilla PPA.  There are lots of reputable guides about this.

I got tired of fighting with snaps on my desktop, so I installed Linux Mint.  

Running remote X11 apps on Ubuntu should work as before, provided you are using X11 as the display server.  I don't know if Wayland works or doesn't.  That would be another line of issues t0 check.
```
echo $XDG_SESSION_TYPE
```
may show the display server.  Here it returns "x11".

I routinely run Mozilla programs remotely over **ssh -X**.  The remote system is running Linux Mint 21.1.  My local system isn't 22.04. I'm on 20.04 for now (needed to match a duplicate system for redundancy).

BTW, my exact command is:
```
$ ssh -X deneb $HOME/bin/firefox.sh
```

The remote script is basically this:
```
/usr/bin/firejail --join-or-start=browserNormal --dns=172.22.22.81  /usr/bin/firefox -no-remote  $@ &
```

I'm not against constrained environments, but I want to control the constraints. Snaps don't allow that, unfortunately.

---

### Post by hemmond on 2023-07-13
Since I have encountered this thread while trying to solve this problem, I will write the solution here. I am regularily using _ssh -Y_ when using SSH with X11 forwarding. 

I have stumbled upon [this linuxquestions.org thread]("https://www.linuxquestions.org/questions/showthread.php?p=6352917#post6352917"). The solution (that worked for me) is giving the firefox snap binary XAUTHORITY environment variable. 

```
XAUTHORITY=$HOME/.Xauthority /snap/bin/firefox
```

P.S.: The linuxquestions thread takes their answer from [this askubuntu question]("https://askubuntu.com/questions/1181046/x-snaps-not-starting").

---

### Post by ActionParsnip on 2023-07-13
Why would you want to do this? Doesn't the system you are connecting from have a web browser?

---

### Post by TheFu on 2023-07-13
> **ActionParsnip said:**
> Why would you want to do this? Doesn't the system you are connecting from have a web browser?

I have a different system just for web browsing, so I don't risk my main system.  It is a security thing, thanks to web browsers being a pile of crap for security.  Just look at the pwn-to-own contests. Every browser fails, every year.  They are big, convoluted, security nightmares of software.  They often don't even implement correctly the things they advertise as "security features."  

I don't trust them and want to keep them away from my production desktop where I make my living.

Not that I need a reason.  Using software over remote X11 has worked for decades. It should still work today. Always.

---

### Post by ActionParsnip on 2023-07-14
> **TheFu said:**
> I have a different system just for web browsing, so I don't risk my main system.  It is a security thing, thanks to web browsers being a pile of crap for security.  Just look at the pwn-to-own contests. Every browser fails, every year.  They are big, convoluted, security nightmares of software.  They often don't even implement correctly the things they advertise as "security features."  

I don't trust them and want to keep them away from my production desktop where I make my living.

Not that I need a reason.  Using software over remote X11 has worked for decades. It should still work today. Always.
I always ask. People come up with hilarious solutions sometimes. 
Have you tried x2go?

---

### Post by TheFu on 2023-07-14
> **ActionParsnip said:**
> I always ask. People come up with hilarious solutions sometimes. 
Have you tried x2go?

I find x2go to be the best of bad options for internet remote desktops and use it that way. I used x2go 24/7 back when I ran Windows as a desktop. These days, I only use it when traveling, usually with chromebook hardware and a limited Linux distro installed. Low-end stuff, but with connectivity.

For LAN applications, remote X11 needs to work, out of the box. 

Snaps have a failure mode that breaks this - I suppose some people might consider it a "security feature".  

I remember when Chromium first was released as a snap and it didn't work remotely on a test install. Plus, snaps don't allow firejail constraints, which I find provide me more control.  I didn't upgrade.  reated a script to address the remotely run Chromium on an older non-snap version from 18.04 with firejail constraints.

Earlier this year, when I needed to move off 18.04, my solution was to install Linux Mint 21.1 to avoid snaps completely.  

In May, I did a fresh install of Server 20.04 onto completely new hardware, then added fvwm and slim as the display launcher. When I need a light browser in this production system, dillo and lynx are my choices. These are mainly to read local html documentation.

As for Wayland, lots of my workflows don't work under Wayland, so that's a non-starter, for now. Some of my workflows are using automation with a browser.  Speaking of which, it is time (Friday morning) to kick off one of those tasks and let it run the next 15 minutes.

Oh and for the OP, the solution NOT to use firefox with the snap distro that I've chosen is to run *Firefox ESR* from the Mozilla PPA. I suppose others might have different requirements.  For me, stability is more important than "new", provided updates/patches are still being provided.

Am I missing something? Maybe people reading have thought of other, useful, ways to run remote browsers over X11Forwarding via ssh that also allows different firejail profiles?

---

