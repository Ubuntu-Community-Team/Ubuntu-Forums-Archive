---
title: "Shutdown/Internet Browsers Brocken"
date: 2008-10-20
forum: Desktop Environments
---

### Post by Zigbigadoorlue on 2008-10-20
Ubuntu 8.4
Firefox 3.0.3
Opera 9.27
Epiphany 2.22.2

Run of the mill hardware, AMD 32bit 2gig processor, ATI 9800pro graphics card

I installed Ubuntu around 7.04 and have been updating since. Things have never worked particularly well especialy graphical stuff which is often slow (particularly in firefox), but usable.

Some new problems have suddenly popped up which I think coincided with the installation of the newest kernel (don't know which, whatever's the newest one to be pushed through update manager.)

Firefox has stopped rendering somethings including the CSS on slashdot.org. The google search bar at the top right no longer works, I'll type somthing and pres enter and nothing happens. Flash has stoped working or tells me to download the most resent version off adobe's sight. I can not do this because the DL button on Adobe's sight doesn't do anything in my browser anymore. 

I'll click on the DL button and nothing happens. I tried to launch Opera and DL it with that browser, and it won't launch. I'll click on the opera icon in Applications, it might think for a fraction of a sec, but it doesn't launch. When typed into Terminal it gives me this

```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
opera: Module initialization failure.  (-2036)
```

I tryed the Epiphany browser and it gave me this:

```
(epiphany-browser:6996): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

followed by this warning pop up:

[B]Could not start GNOME Web Browser
Startup failed because of the following error:
Failed to create directory “/home/katz/.gnome2/epiphany”.[/B]

Both browsers work with sudo for some reason.

I can no longer Shutdown with the shutdown button, I'll click it and, without giving me any prompt, everything on the desktop except the background picture will disappear. I then have to enter Terminal and shutdown manually. 

I tried saving some text into a file on my desktop and it gave me this

[B]Could not save the file /home/katz/Desktop/new file.
There is not enough disk space to save the file. Please free some disk space and try again.[/B]

There is plenty of room on my hard drive and it was only a few lines of text worth of data.

None of this things are aliviated by using a earliar saved Kernal. Because Epiphany and Opera only worked under sudo it makes me think my permisions have been screwed up somehow (why would that not let me use parts of firefox? I have no idea) Could this be a result of the new kernel/what ever else was updated? 

Pleas help I don't want to go back to using my windows partition which is even more screwed up. But at least I can use the interwebs on it. 

Much love
Rowan

---

### Post by DrLaunch on 2008-12-25
I think I'm having the same problem. Programs like The Gimp, Opera and Firefox stop working properly. Opera says it "couldn't save file" for files like /home/username/.opera/bookmarks.adr, notes.adr and more. I can't save images in The Gimp, and the search field in Firefox isn't working. I'm having similar CSS rendering problems, but on the Ubuntu Forums.

It happened after I downloaded and installed a bunch of games such as Alien Arena, Armagetron Advanced, Frozen Bubble, lbreakout 2, Nexuiz, Planet Penguin Racer, SuperTux 1 and 2, Torcs and Wormux.

I had this problem on the same computer earlier and I reinstalled Ubuntu. Now it has returned.

Now to what variables could have had an effect on this problem:

I have an Asus Eee 900. In order to make the wireless work, I had to install the custom Linux kernel from Array.org. I've opened it and voided my warranty by switching the hard drive as well.

I'm running Ubuntu 8.10 and have installed Compiz Configurator, some new panel applets and Avant Window Navigator. I've installed some more stuff but I'm not going to bother making a list.

Basically the problem makes it impossible to write to files, at least with my current user level.

This problem is very real and I'm sure people are experiencing it. I hope someone knows how to fix this problem.

---

### Post by RJARRRPCGP on 2008-12-27
Looks like the permissions were borked.

---

### Post by stderr on 2008-12-28
I was about to say you're definitely out of disk space, then you said you weren't...

Are you *sure*? This rings bells with me when that happened before, and it makes sense with sudo working for those progs.

Are you certain that your *home* partition isn't full? If you run this in a terminal:

```
df -h | grep home
```

what does it produce?

e.g. my laptop (Ace5) gives

/dev/sda7             9.2G  4.1G  4.7G  47% /home

Meaning 47% free space, 4.7GB available, 9.2GB total partition size.

If you haven't got a separate home partition, then it'll just be the root partition that matters.

---

### Post by albinootje on 2008-12-28
> **Zigbigadoorlue said:**
> 

[B]Could not start GNOME Web Browser
Startup failed because of the following error:
Failed to create directory “/home/katz/.gnome2/epiphany”.[/B]

Both browsers work with sudo for some reason.


If they work with sudo, but not for the normal user, then that really sounds like a free disk space problem.

Can you post the output of :
```

df -h

```

---

