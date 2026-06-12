---
title: "Restart LXQt desktop?"
date: 2020-10-03
forum: Desktop Environments
---

### Post by pdh0710 on 2020-10-03
Hi... (Please excuse my English)

I just installed Lubuntu 20.04. I want to boot Lubuntu without turning on monitor,
and turn on monitor only when necessary. But, when I turned on the monitor of
booted Lubuntu(auto login), LXQt desktop was not displayed at all. What I see was
only black blank screen.
I connected to the Lubuntu using SSH and tried to wake up LXQt desktop, but can't.
The only thing I could do was reboot using SSH terminal.

There is a guide to [restart various Linux desktop]("https://www.maketecheasier.com/restart-frozen-desktop-linux/"), but LXQt is missing.
How can I restart LXQt desktop when lately turning on monitor?

---

### Post by ajgreeny on 2020-10-03
Do you have autologin already set up, ie, login without  a password  being asked for?
If not, the system will get to the login screen and eventually that display will turn off unless a password is entered.

It may be possible to stop that occurring  but I'm not sure how without searching.

See if this thread is any help.
[https://ubuntuforums.org/showthread.php?t=2283523](https://ubuntuforums.org/showthread.php?t=2283523)

---

### Post by pdh0710 on 2020-10-03
Yes, I set up my Lubuntu to autologin(I edited my post) and to run screen saver in idle time.

---

### Post by ajgreeny on 2020-10-04
Does the screensaver need a password when you come out of it, or does the desktop lock automatically?

---

### Post by pdh0710 on 2020-10-05
No.
Actually, I tried it 1 minute after my Lubuntu booting, for test.
But the result was same, the black blank screen.
So I should reboot my Lubuntu using SSH.

---

