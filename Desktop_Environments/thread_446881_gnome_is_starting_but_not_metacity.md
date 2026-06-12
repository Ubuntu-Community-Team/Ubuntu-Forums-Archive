---
title: "gnome is starting but not metacity"
date: 2007-05-17
forum: Desktop Environments
---

### Post by mority on 2007-05-17
Since a restart of my notebook with Ubuntu 7.04 I have a strange problem: After I log in with gdm, gnome is starting up but it does not load metacity! So I have the panels and see the background image and I can launch applications via the menu but I don't have any windows. When I start an application it starts without any window handles and without a title bar.

I don't know much about the internals of gnome and I have no clue how to debug this, so I would very much appreciate any help or hint.

---

### Post by bmartin on 2007-05-17
This sounds like what happened when I was loading **Beryl** automatically in my Gnome session and it was failing to start properly. What happens if you type **metacity** in a terminal? Does Metacity load properly? You could always throw that into your startup programs as a quick fix... if you're running Beryl and this is happening, it's probably a problem with your xorg.conf file or Emerald, which is what provides Beryl's window decorations.

---

### Post by newlinux on 2007-05-17
I've also seen in Feisty that if I don't close firefox before shutting down or logging out the next time I log in metacity isn't started. I think this is a documented bug.

---

### Post by mority on 2007-05-17
I started metacity manually and it worked normally. Now it starts up again automatically after logging out and in again, too. I still have no clue what exactly was going wrong but at least it's working again. The hint to start metacity manually was very valuable.
Thanks for you help, guys!

---

### Post by bmartin on 2007-05-17
You're welcome. I've only had to run Metacity manually due to Beryl problems; I wasn't aware of the Firefox bug and I've killed my X session with Firefox running many times. Maybe it's a certain combination of video settings and Firefox that causes this kind of problem.

---

### Post by newlinux on 2007-05-17
> **bmartin said:**
> You're welcome. I've only had to run Metacity manually due to Beryl problems; I wasn't aware of the Firefox bug and I've killed my X session with Firefox running many times. Maybe it's a certain combination of video settings and Firefox that causes this kind of problem.

Probably. I'm using the nvidia binary driver. I don't remember the particulars, but it definitely doesn't happen to everyone.

---

### Post by mority on 2007-05-18
I had a Firefox session open when I rebooted before the problem occurred. But I'm pretty sure that I killed X sessions while having an open Firefox session before and nothing bad happened. Maybe I did it now the first time after the upgrade to 7.04. Dunno...

---

### Post by newlinux on 2007-05-18
End of this thread has info on this issue:

[http://ubuntuforums.org/showthread.php?t=427268](http://ubuntuforums.org/showthread.php?t=427268)


[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350)

Not just firefox, but other session-unaware apps will do this as well...

---

