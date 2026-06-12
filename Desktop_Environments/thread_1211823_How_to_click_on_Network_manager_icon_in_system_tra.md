---
title: "How to click on Network manager icon in system tray from terminal"
date: 2009-07-13
forum: Desktop Environments
---

### Post by brad_pitt on 2009-07-13
Hi All,

I am using ubuntu 9.04 and i have a need.

I want to click on Network manager icon in system tray from terminal using a command or script.

Is it possible? Please help me on how to do this

Regards
Brad

---

### Post by quixote on 2009-07-15
I believe the command is
**nm-applet**

Not sure if that's what you mean.

---

### Post by Pziko on 2009-07-15
Interestingly, I'd come here for more or less the same reason. 

I've been tinkering quite a bit with Gnome and KDE, and just recently did a completely fresh install of Ubuntu, downloaded and installed KDE4 as well as a number of apps. When I switched over to KDE, I found I was no longer connected to the internet, and the network settings / system settings had nothing regarding wireless connections. 

I ran nm-applet and it worked like a charm, however I can't seem to find any way to keep it on the dock. Is it possible to have that start on login while using KDE?

---

### Post by Brandon Williams on 2009-07-15
> **brad_pitt said:**
> I want to click on Network manager icon in system tray from terminal using a command or script.

It's not completely clear what you're trying to do. Why do you need your script to simulate a click on the icon? Is it just to make the list of wireless networks pop up so that you can further control the pop up menu using the keyboard? Or are you looking to simulate other GUI activity in your script after the pop up menu appears?

What I'm getting at is that if you are trying to control network manager settings from a script, simulating GUI actions will probably not be the most straightforward way to do it. If we had a better idea of what you're trying to do, we might be to give better advice.

---

### Post by brad_pitt on 2009-07-16
Once my network connection is disconnected network manager applet does not try to connect to the network connection.So i am planning to write a script which checks when network is disconnected and clicks on the network manager in the system tray..

the command nm-applet is not doing what i am looking for

Any other commands will be helpful

Thanks guys for your time and suggestion

---

