---
title: "Not Getting (helpful) Replies"
date: 2005-03-19
forum: Desktop Environments
---

### Post by watchitman on 2005-03-19
I've posted a fair number of questions on this forum and very few of them are getting replies. I've seen the very same thing happen in many other threads by other people. It usually concerns gaming and joystick support. Some have to do with GTK+ 1.x. Why is this? Doesn't ANYONE know anything about this stuff? Where are the answers to things like:

* Getting a permanent link to stay in /dev/js0
* Does FCEU have joystick support?
* Changing the font and font size in GTK+ 1.x applications

Anyone? I mean come on, this stuff is there and I know many other people want to know besides some answer like "use a GTK 2 app" or "don't do that." Where is the helpful Ubuntu community I keep hearing about? Where are the answers?

---

### Post by Buffalo Soldier on 2005-03-19
[QUOTE=watchitman]* Getting a permanent link to stay in /dev/js0
* Does FCEU have joystick support?
* Changing the font and font size in GTK+ 1.x applications?[/QUOTE]

I guess the reason for the lack of response for the first two problem is that not many are running Ubuntu for games.

About the GTK 1 apps, I have to surrender. I have no idea about configuring GTK 1 apss. Sorry.

Edit: I had the opposite problem with XMMS. Fonts were too small. Using rhthymbox now.

---

### Post by WW on 2005-03-19
For your question about /dev/js0: I don't know how to do it, but I have seen similar questions about dvd drives, and the answer involves udev (perhaps adding an appropriate entry in /etc/udev/udev.rules, or something like that).  That's not an answer, but it might give you some additional terms to search for.

Sorry, I can't help you with the other questions. (I don't even know what FCEU is!)

---

### Post by az on 2005-03-19
People in Ubuntu tend to not use gtk1 apps anymore.  Gtk 1 is very well documented on the internet.  Bumping your posts instead of spending five minutes on google does not make anyone really want to go out of their way for you.

I looked at a number of your threads.  Most seem to have been answered nicely.

I wouldn't have said anything, though, if you had not started this thread...

---

### Post by rah on 2005-09-03
fceu does have joystick support.

Open a shell and try the following:

fceu inputcfg gamepad1 [filepath]

Before loading your rom, it should ask you to configure your buttons; you only need to do this once.

I hope this works for you.

---

