---
title: "Help: Using x11vnc and ssvnc with ESD for remote desktop with audio"
date: 2010-08-11
forum: Desktop Environments
---

### Post by tehowe on 2010-08-11
Hey Ubuntu gurus;

This seems challenging.

At the moment I'm running Putty on a windows box at work to SSH in and tunnel port 5900, then I execute 

```
x11vnc -xkb -ncache 10 -safer -localhost -nopw -once -display :0
```from the shell.

I run ssvnc and tell it to connect to localhost, and we're good for remote desktop.

**The next step is to push my luck and see if I can get streaming audio as well.**

Can anyone help?

ssvnc is supposed to automate many of the required processes, making the use of a standalone ssh client like Putty redundant - it bundles a similar program, passing commands through ssh from its GUI

Under options/advanced it has a facility to 'Enable ESD/ARTSD' audio tunnelling and it bundles a windows-executable (using cygwin library) version of ESD, so it just needs some configuration.

When you click that option there's a documentation pane that says you can put 

> esddsp -s localhost:16001 gnome-sessionin your ~/.xsession startup file but since I use my Lucid box for local sound as well I'm not sure that's ideal as I want to use JACK, etc. and it looks like this command would route all audio to network, all the time.

ssvnc suggests using "x11vnc -create" mode to start it up in a virtual X session through Xvfb but it doesn't really go into any more detail as to how you do this.

I've installed Xvfb through synaptic, and that's as far as I've gotten. I can't figure out what the correct -create switches might be.

Any ideas how to get this working?

---

### Post by krunge on 2010-08-11
Do you want to view the desktop on the physical hardware (video card, monitor, etc.) or do you not mind if the desktop is virtual (e.g. Xvfb)?  Do you really not care which you do?

It is easier to redirect audio in a virtual desktop, and, as you say, always to the network.

---

### Post by tehowe on 2010-08-11
> **krunge said:**
> Do you want to view the desktop on the physical hardware (video card, monitor, etc.) or do you not mind if the desktop is virtual (e.g. Xvfb)?  Do you really not care which you do?

It is easier to redirect audio in a virtual desktop, and, as you say, always to the network.

Hi Karl;

As long as running a virtual desktop for the remote connection isn't painfully slow, it doesn't really matter. And if that means it doesn't show up on the notebook's physical LCD screen when I'm away, so much the better. (Just so long as I can use it normally when I get home.)

PS Great tool, thanks for making it available.

---

### Post by krunge on 2010-08-11
> **tehowe said:**
> 
As long as running a virtual desktop for the remote connection isn't painfully slow, it doesn't really matter.
It should be pretty fast actually, usually much faster than an X desktop on physical hardware.
> And if that means it doesn't show up on the notebook's physical LCD screen when I'm away, so much the better.

Yes, it certainly won't show up.
> 
(Just so long as I can use it normally when I get home.)

Well, that is the point of my question. You won't be able to see it at all (i.e. when you get home and are sitting at the physical display) except via VNC.

It is possible to view the desktop on the local physical display, but you need to use a VNC viewer.  I do this all the time in a seamless way, but most people wouldn't like it.  Details here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#infaq_localaccess](http://www.karlrunge.com/x11vnc/faq.html#infaq_localaccess)[/INDENT]

BTW I have been using the ssvnc/x11vnc ESD hack for about a year (including today at work) to have the Skype notification sounds come to me where ever my VNC viewer is.  I don't do Skype voice thru ESD though, the audio is not compressed in ESD!

---

