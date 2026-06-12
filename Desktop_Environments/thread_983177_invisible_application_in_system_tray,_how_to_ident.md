---
title: "invisible application in system tray, how to identify?"
date: 2008-11-15
forum: Desktop Environments
---

### Post by helwitch on 2008-11-15
So, there's clearly an application in my system tray (blank space between wireless&battery in below pic), but it's got no icon, and nothing happens when I right click it. How do I find out what application it is and make it show an icon or not sit in the system tray? logging out and back in, manually restarting the xserver, even rebooting all don't fix this. KDE3 on 8.04
[IMG]http://pics.livejournal.com/heldc/pic/0007rytk[/IMG]

---

### Post by GeneralZod on 2008-11-15
On a hunch, I'd suggest that it's possibly the adept updater.

---

### Post by helwitch on 2008-11-15
I sigtermed adept_notify, blank space is still in the systray. Good idea tho, thanks just the same.
So, I've figured out it's an instance of python, cos it goes away when I sigterm python in ksysguard. This instance of python is eating my CPU when it's running too. How do I find out what's loading this python and make it stop?

---

