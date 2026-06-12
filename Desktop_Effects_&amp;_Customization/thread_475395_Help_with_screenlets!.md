---
title: "Help with screenlets!"
date: 2007-06-16
forum: Desktop Effects &amp; Customization
---

### Post by andrewsomething on 2007-06-16
I had been using gDesklets for a long time with no problems, but I decided to try to switch over to Screenlets since it looks much nicer. I'm running into many problems, and hoping that I can find some help.

I can't seem to get the ones I want to launch on start up to run every time. Screenlets will work fine if I start them individually, but it seems random which ones will come back on start up. The ones that will show up keep their themes, but don't seem to remember their window settings (ie sticky, stay below, ect). 

Also changing windows setting from the context menu doesn't always change the same settings in the properties menu.

I have "screenlets-tray" set to run on start up. Is there a different command that I should be using, or do I need to run multiple commands? 

And, the now playing screenlet won't work for me at all. 

Any help would be greatly appreciated!

---

### Post by master5o1 on 2007-06-16
I'm not much help, but I am having the same problem... exactly!

I have my clock, system stats, calender and control -lets on ... and yes, random to which starts up.

Also, mine reset and randomise (dissappear/reappear randomly) when I restart the window manager (using beryl manager menu). Argh!

---

### Post by master5o1 on 2007-06-16
Oh, and do you get this random grey box of about 200px square pop up every now and then?

---

### Post by andrewsomething on 2007-06-16
Ya, I've gotten that as well. 

I'm willing to accept that there are going to be some things that are a bit buggy, but if the problems that I'm having are normal I can't believe anyone would use screenlets. So either I'm doing something wrong, there's a work around, or there are a lot of people that use screenlets just long enough to take a screenshot....

---

### Post by andrewsomething on 2007-06-16
> **andrewsomething said:**
>  And, the now playing screenlet won't work for me at all. 

Well, one problem down. I should have been able to come up with this one on my own, but buried in a thread on the Beryl forum I found my answer for my "Now Playing" problem.

In order to run the "Now Playing" screenlet with Amarok, you must install "python-dcop" (which can be found in Synaptic). Amarok, being a KDE program, uses a Dcop backend. "Now Playing" was originally written with Dbus in mind, but someone added support for Amarok if "python-dcop" is installed.

---

