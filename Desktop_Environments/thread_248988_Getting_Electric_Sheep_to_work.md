---
title: "Getting Electric Sheep to work?"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Padraic on 2006-09-01
I installed electric sheep 2.6.4-2 from synaptic.  I can select electricsheep from the list of available screensavers in gnome-screensaver but all I get is a black screen.  I did read somehwere that the initial download can take awhile, but it's been a week, I would've expected something by now.  If anyone has gotten it to work can you please tell me how?  Thanks!

Patrick

---

### Post by Greycloak on 2006-09-01
I've been running it using xscreensaver. It's available in the repos, and it runs opengl screensavers a lot better (at least for me). Electric Sheep seems to work fine, although the first sheep does take a long time to download.

---

### Post by Tonren on 2006-09-06
Hey Patrick, did you ever get Electricsheep working?  I can't seem to get it working, myself.

---

### Post by Anduu on 2006-09-07
I had been having troubles getting it to work as well...that version in the repos is older than dirt.I don't even know if it is compatible with their servers anymore.

To get it to work here is what I did.

Set the settings for electricsheep the way you want them before you do anything as you will lose this ability once you have completed this.You will still be able to control the blank time etc just not the specific electricsheep settings.**Note** the electricsheep command line is still available in advanced settings if you know what you are doing.

Follow instructions here to replace GnomeScreensaver with XScreensaver...I will not appear in the GnomeScreensaver list for some reason.
[http://www.ubuntuforums.org/showthread.php?t=195557&highlight=replace+screensaver](http://www.ubuntuforums.org/showthread.php?t=195557&highlight=replace+screensaver)

Go here
[http://electricsheep.org/index.cgi?&menu=download](http://electricsheep.org/index.cgi?&menu=download)
and download version 2.6.8 for RedHat Linux...the Debian one will not work with Ubuntu as it requires a higher version of libc6 than is available/safe for Ubuntu.

Convert the rpm to deb via Alien:
```
sudo alien electricsheep-2.6.8-1.i386.rpm

```

Install by whichever means you prefer...I use GDebi.

Go to /home/username/.sheep and delete anything in here...not sure if it is nescessary but I did just to avoid possible version conflicts...

Then from a terminal run
```
xscreensaver-demo
```
and select electricsheep.**Note** you will have very limited options for configuring electricsheep unless you know the command line.
Be sure to set "Cycle after" in the settings to it's maximum...ie 720

Now it "should work" as advertised..let it run overnight and enjoy your sheep :))

Let me know how this works for you all...if it works well I guess I should do an official how-to ;)

---

### Post by wikinator on 2006-11-07
This worked for me, except that the screensaver only takes up a quarter of the screen in the upper left-hand corner.  I wonder how this might be solved.

---

### Post by Anduu on 2006-11-07
> **wikinator said:**
> This worked for me, except that the screensaver only takes up a quarter of the screen in the upper left-hand corner.  I wonder how this might be solved.

Make sure --zoom 1 is in the command line under advanced settings.

Another thing...on my machine selecting preview will not let electricsheep go fullscreen.If I let it activate on its own it goes to fullscreen as it should.

---

### Post by chadlongstaff on 2008-04-18
I had this problem again with Hardy. My solution was to delete the symlink to /usr/bin/electricsheep from /usr/lib/xscreensaver/electricsheep. Replace with a script calling /usr/bin/electricsheep --mplayer 1 --zoom 1. Works nicely and no need to change the default screensaver backend; slight problem with a wee blue square in the top right hand corner, but I'm ignoring that for now ;)

---

### Post by EReckase on 2008-06-27
This should be fixed in the latest version, available from

deb [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main

---

### Post by chronographer on 2008-06-28
Can I limit the times electric sheep downloads? I have limited downloads during the day... lots over night. I would love to be able to turn off the downloads during the day.

---

