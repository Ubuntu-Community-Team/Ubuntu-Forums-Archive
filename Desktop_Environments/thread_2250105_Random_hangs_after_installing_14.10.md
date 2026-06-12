---
title: "Random hangs after installing 14.10"
date: 2014-10-26
forum: Desktop Environments
---

### Post by JBudOne on 2014-10-26
Just like the title says.. This occurs seemingly randomly (typing in vim, typing in the terminal), and frequently (4 times this morning, and 3 times last night). Dmesg shows nothing of interest either.. Each time it occurred right in the middle of me typing. X seems to hang, however my mouse is still working fine and music playing from chrome or banshee continue to play fine. Trying to switch to another workspace (ctrl+alt+f2-f8) results in the mouse disappearing and any sound stopping, and from there I can't do anything but magic SysReq. I'm pretty stuck guys :(  I'm not really sure what this could be or where to even start looking. I've tried switching between nvidia and nouveau drivers, but that doesn't make any difference. Any thoughts or tips are really very helpful, thanks!

---

### Post by JBudOne on 2014-10-26
**Breaking news!**
It just happened again, and I was able to go onto my laptop and ssh into the system. Everything still seems to be working fine through ssh, however top doesn't show any of the programs that I had previously running. After 5-10 minutes of snooping around through ssh, I heard that drum-beat login sound from Ubuntu from the PC (indicating that I've logged out I guess?), however the screen is still stuck in the same frozen state

---

### Post by JBudOne on 2014-10-27
**Updates**
[LIST]
[*] Updated to bleeding edge X....same problem
[*] Downgraded to Ubuntu 14.04 LTS.....same problem
[/LIST]

Note: Ubuntu 14.10 was using X v1.16, and 14.04 is using 1.15.1.

---

### Post by jonnylinuxnerd on 2014-10-30
I've been having similair issues that appear when VT switching but I'm using an Intel GPU instead of NVidia :/ I can SSH when these hangs happen and interestingly the keyboard NumLock still works as well as SysReq key bindings but I'm not entirely sure what the problem is. Killing compiz can help sometimes but the randomness of the issue makes it harder to understand :/

---

### Post by JBudOne on 2014-11-15
**Fixed?**

I downgraded to 13.10 for a couple of weeks and had no problems until the end my system started crashing (keyboard, mouse, ssh don't work). I was suggested to update my BIOS and upgrade to 14.04, and haven't had any problems so far this time.

Chipset: P8Z77-V LK
old driver: v0904 (oct 2012)
new driver: v1402 (mar 2014)

---

### Post by jonnylinuxnerd on 2014-11-15
I know you said you were using nvidia but are you in a dual GPU optimus situation with the intel gpu actually being used to primarily render the desktop? If so it may be worth checking this bug out as it seems similar [https://bugs.launchpad.net/bugs/1384342](https://bugs.launchpad.net/bugs/1384342) :)

---

### Post by JBudOne on 2014-11-23
> **jonnylinuxnerd said:**
> I know you said you were using nvidia but are you in a dual GPU optimus situation with the intel gpu actually being used to primarily render the desktop? If so it may be worth checking this bug out as it seems similar [https://bugs.launchpad.net/bugs/1384342](https://bugs.launchpad.net/bugs/1384342) :)

Sorry! I didn't notice this reply until now. This isn't the case for me sadly, but was this the problem you were having? It should be helpful for anybody else viewing this thread. Sadly I've had a problem in 13.10 and 14.04 again with a system crash (no keyboard, mouse, sound or ssh access). The issue is kind of rare though, but I'll post updates w/ logs the next chance I get

---

### Post by ghoru on 2015-08-25
> **JBudOne said:**
> **Fixed?**

I downgraded to 13.10 for a couple of weeks and had no problems until the end my system started crashing (keyboard, mouse, ssh don't work). I was suggested to update my BIOS and upgrade to 14.04, and haven't had any problems so far this time.

Chipset: P8Z77-V LK
old driver: v0904 (oct 2012)
new driver: v1402 (mar 2014)

Same problem, same motherboard. New BIOS don't helps (v1402 (mar 2014)).

---

### Post by JBudOne on 2015-08-25
> **ghoru said:**
> Same problem, same motherboard. New BIOS don't helps (v1402 (mar 2014)).

Thanks! I've since switched over to Fedora and experience the same problems. It *appears* to be less frequent than on Ubuntu, but that may just be my wishful goggles working. I also noticed that I could *sometimes* recreate the issue by having a lot of tabs open on Chrome, however this could be a completely unrelated issue. Some of my research pointed me towards a potential GPU issue; so it may be worth noting that I'm using a GTX 550 Ti.


**Edit**:
I was also told that it may be a hard drive problem. So I got a new hard drive, and this did nothing to help the problem.

---

### Post by ghoru on 2015-09-01
> **JBudOne said:**
> Thanks! I've since switched over to Fedora and experience the same problems. It *appears* to be less frequent than on Ubuntu, but that may just be my wishful goggles working. I also noticed that I could *sometimes* recreate the issue by having a lot of tabs open on Chrome, however this could be a completely unrelated issue. Some of my research pointed me towards a potential GPU issue; so it may be worth noting that I'm using a GTX 550 Ti.


**Edit**:
I was also told that it may be a hard drive problem. So I got a new hard drive, and this did nothing to help the problem.

I've switched to Gentoo and have not any problems. Also 14.10 with KDE installed works perfect on this PC.  Only Unity were hangs.

PS. GTX 660 Ti

---

