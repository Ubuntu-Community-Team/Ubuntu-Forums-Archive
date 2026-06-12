---
title: "&quot;Network Disconnected&quot; popup after sleep, not disappearing"
date: 2011-07-02
forum: Desktop Environments
---

### Post by geek113377 on 2011-07-02
I am running Xubuntu 11.04. A popup that reads "Network Disconnected - You are now Offline" appears every time I disconnect from a wifi network.
[ATTACH]196565[/ATTACH]
This is normal and OK. Every time I suspend my computer, it disconnects from the network. This is normal and OK. When the computer wakes up, it displays the popup. This is annoying. This popup does not just fade out like all the other ones, I have to manually close it. This is very annoying. The very first time the popup appeared, after installing Xubuntu, the popup had 3 buttons that all read "Don't show this popup again," I clicked all of them, hoping that one would work. apparently they didn't. How do I get that popup to not show up after going to sleep, but still appear under other conditions. If that isn't possible, how can I make it automatically fade away/disappear? Please help, answers appreciated.

---

### Post by Toz on 2011-07-02
I've seen this as well. There is a bug report for it: [https://bugs.launchpad.net/ubuntu/+source/notification-daemon/+bug/606825]("https://bugs.launchpad.net/ubuntu/+source/notification-daemon/+bug/606825")

See also: [http://ubuntuforums.org/showthread.php?t=1750183&highlight=xubuntu+notification]("http://ubuntuforums.org/showthread.php?t=1750183&highlight=xubuntu+notification")

---

### Post by steevven1 on 2011-10-17
I am also experiencing this. Looks like the actual bug is here: [https://bugs.launchpad.net/ubuntu/+source/xfce4-notifyd/+bug/835972](https://bugs.launchpad.net/ubuntu/+source/xfce4-notifyd/+bug/835972)

---

