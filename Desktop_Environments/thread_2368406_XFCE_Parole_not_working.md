---
title: "XFCE Parole not working"
date: 2017-08-10
forum: Desktop Environments
---

### Post by asif-bahrainwala on 2017-08-10
Hi 
Parole is not working on XUbuntu 17.04

I keep getting the error:

GStreamer backend error
could not initialize Xv output 


When running the following command
/usr/share/parole$ parole --xv false

** (parole:13021): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-xrXBKBiLXF: Connection refused
Unknown option --xv
Type parole --help to list all available command line options


How do I fix this.
I am running this on Oracle Virtual box. Please advise

---

### Post by QIII on 2017-08-10
Hello!

Instead of the double dash, try a single one.  Let us know how that goes.

---

### Post by #&amp;thj^% on 2017-08-10
> **asif-bahrainwala said:**
> Hi 
Parole is not working on XUbuntu 17.04

I keep getting the error:

GStreamer backend error
could not initialize Xv output 


When running the following command
/usr/share/parole$ parole --xv false

** (parole:13021): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-xrXBKBiLXF: Connection refused
Unknown option --xv
Type parole --help to list all available command line options

How do I fix this.
I am running this on Oracle Virtual box. Please advise
Try this from a terminal in the VB
```
parole &#8211;xv false
```
any better?
Ninje'd by QIII :)

---

### Post by asif-bahrainwala on 2017-08-10
Hi,
I did all sorts of combinations including the single dash, nothing works :-(

---

### Post by asif-bahrainwala on 2017-08-10
nope....

---

### Post by asif-bahrainwala on 2017-08-10
I installed Totem/videos, that works (so it doesn't seem to be a GStreamer issue), that works , parole still doesn't work

---

### Post by QIII on 2017-08-10
What was the message that time?

---

### Post by asif-bahrainwala on 2017-08-10
asif@asif-VirtualBox:/usr/share/parole$ parole -xv false

** (parole:14866): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-xrXBKBiLXF: Connection refused
Unknown option -xv
Type parole --help to list all available command line options

---

### Post by asif-bahrainwala on 2017-08-10
Do you all have had a similar problem with parole

---

### Post by #&amp;thj^% on 2017-08-10
Well in Parole try under Tools>> Display>>X Window System (No Xv)

---

### Post by asif-bahrainwala on 2017-08-10
Hi,
that did the trick, but I don't understand....what is that...

---

### Post by #&amp;thj^% on 2017-08-10
Just another way to force Parole not to use the  X ( Xv) is all.
support for double buffering with the X11/XV video outputs, and the ability to load plugins by name instead of full path.
To answer your other question:
> Do you all have had a similar problem with parole 
It has been a very common problem reported.
Cheers

---

### Post by asif-bahrainwala on 2017-08-10
That did it....but I dont understand....what is it

---

### Post by asif-bahrainwala on 2017-08-10
Is it because I need to install some XWindow extensions or I have a missing driver or I am inside virtual box

--xv
 Enables/Disables the X video extension for the X Window System (true or false, default=true)

anyways....super thanks......

---

### Post by #&amp;thj^% on 2017-08-10
Your Welcome ;)
No just parole code need to be fixed this was released in Feb/2017 so I would expect it to get fixed soon enough.(Not sure when or If )

---

### Post by flocculant on 2017-08-11
> **1fallen said:**
> Your Welcome ;)
No just parole code need to be fixed this was released in Feb/2017 so I would expect it to get fixed soon enough.(Not sure when or If )

I believe it's fixed - at least the version in 17.10 works here when I use it.

However - "I would expect it to get fixed soon enough" - unlikely.

To do that we need to [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") it. Given the nightmare it was for us to get the SRU through for Thunar ([lpbug]1679488[/lpbug]) - fixing this with an SRU when people can set it locally is unlikely to happen.

As an aside to that - we're constantly trying to get people to test the dev version of Xubuntu AND it's packages - and we are lucky if we see 6 or 7 people do that and report it where we see it.

---

