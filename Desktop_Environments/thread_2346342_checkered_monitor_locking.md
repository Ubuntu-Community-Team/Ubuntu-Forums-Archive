---
title: "checkered monitor locking"
date: 2016-12-13
forum: Desktop Environments
---

### Post by dgermann on 2016-12-13
Friends--

Symptoms: monitors go all checkered in multiple colors, sometimes locking the machine. Seems to happen about 2 or 3 times an hour.

System: 16.04, new install, using full disk encryption as offered on install disk, nothing fancy or out of the ordinary on the luks side. Three monitors. Installed Ubuntu 16.04, then installed ubuntu-gnome-desktop. No gaming, mainly run LibreOffice Writer and Calc.

When it happens: I have noticed it happens when I move the mouse pointer to the upper left, usually on the middle screen. (Left hand screen is primary, where the gnome favorites are; I have turned off the upper left hot spot.) It did happen once when I came back to the screen saver and lock (ctrl-alt-L): the screens were all checkered before I could enter my password.

I can usually enter things on the documents and spreadsheets, and do things like save documents while the screen is checkered.

What usually works: alt-f2, r <ret>

Sometimes it will lock the whole computer, with or without the checkered pattern. I cannot then do ctrl-alt-f1, ctrl-alt-backspace (yes, I turned that on), nor ctrl-alt-del. I can ssh into the machine and do a sudo reboot, and other things there.

What does not work: sudo service lightdm restart, nor sudo killall -3 gnome-shell, nor gnome-shell --replace.

Could this be a bad graphics card? Although until a couple weeks ago, I was running 12.04 lts without any problems....

Thanks!

---

### Post by dgermann on 2016-12-19
Friends--

A report and I will mark this solved.

An additional symptom: one time when it froze, there were on the screens things that looked like broken shards of glass, each with a part of a screen that had been up on the monitors some time that day, but not in the work that was left up just before the freeze. Some spreadsheets, some word processing documents, some email, some browser stuff. Just things I had been working on that day. Strange.

One valuable clue I had was that no one here responded, although a bunch of you looked. That told me that this problem was not a common one, so probably it belonged just to me. Therefore, check out the hardware.

So I called my hardware people and they said that it could be a bad graphics card. I replaced that with a gtx 1060, and all is working well now.

So a thank you to you denizens of the forum: you actually did help. I hope my report can help someone else!

---

