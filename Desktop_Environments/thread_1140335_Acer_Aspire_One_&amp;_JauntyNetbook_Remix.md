---
title: "Acer Aspire One &amp; JauntyNetbook Remix"
date: 2009-04-27
forum: Desktop Environments
---

### Post by johnaaronrose on 2009-04-27
On my 8gb ssd netbook: I've upgraded BIOS to 3309 OK: I forget where suggested.

Fan control OK as per Community documentation usingh new kernel module acerhdf.

Optimized SSD by noatime option in Community documentation.

Reduced SSD wear by moving logs to temporary file system as per Community documentation.

Disabled scrollkeeper (to improve install packages speed) as per Community documentation.

I'm undecided about doing (as per community documentation): what do you think?
Allowing top of a window to be dragged above top of screen to improve handling of tall windows.
To prevent unintended use of touchpad: disable all scroll and tap commands for 1 second after each keystroke.
Tweak for bootup speed: by concurrency=shell 

Major outstanding issue is getting Skype to work. I've fiddled with Gnome Volume Control, Sound In Preferences, and Skype Options Sound Devices. But got nowhere: Skype gives Audio Playback problem. Anybody solved this?

PS Community documentation is at:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by craiggc on 2009-04-30
i have skype working fine - i did need to change the sound options tho - i will check as to what when i get home - but i just played around and it started working.

---

### Post by Clogger on 2009-04-30
> **johnaaronrose said:**
> On my 8gb ssd netbook: I've upgraded BIOS to 3309 OK: I forget where suggested.

Fan control OK as per Community documentation usingh new kernel module acerhdf.

Optimized SSD by noatime option in Community documentation.

Reduced SSD wear by moving logs to temporary file system as per Community documentation.

Disabled scrollkeeper (to improve install packages speed) as per Community documentation.

I'm undecided about doing (as per community documentation): what do you think?
Allowing top of a window to be dragged above top of screen to improve handling of tall windows.
To prevent unintended use of touchpad: disable all scroll and tap commands for 1 second after each keystroke.
Tweak for bootup speed: by concurrency=shell 

Major outstanding issue is getting Skype to work. I've fiddled with Gnome Volume Control, Sound In Preferences, and Skype Options Sound Devices. But got nowhere: Skype gives Audio Playback problem. Anybody solved this?

PS Community documentation is at:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

I am having the same Skype volume issue with audio playback.  Any help appreciated.  Not sure if it's relevant but the system sounds are not working either (themes) UNR

---

### Post by StarWarrior on 2009-05-11
may I ask what your bootup time is? I am quite fond of the fast bootup time of the preinstalled Linux, but I fancy Ubuntu, because it is much nicer.

---

### Post by jacktar on 2009-05-11
The boot time of UNR is longer than Linpus, however, when the system is up it is already connected to your wireless connection. So the time involved is about the same.

---

### Post by pling on 2009-05-11
> **jacktar said:**
> The boot time of UNR is longer than Linpus, however, when the system is up it is already connected to your wireless connection. So the time involved is about the same.

I'd disagree with that. And I would add that Remix was the slowest distro I've tried for everything - apps opened slowly and Firefox seemed slow. I was going to take some measurements but I first I thought I should update the OS to be as fair as possible - that was when things went really bad and both GUI modes messed up, with stuff like window top bars and the main menu disappearing. 

The one excuse I can think of is that I did have a BIOS a few numbers behind. I updated the BIOS but the problems continued. Theoretically it would have been interesting to know if Remix would then have run, but I felt it was time to move on.

My other comment would be that a Netbook OS should let you make any app you choose full screen - as in no borders or desktop GUI - with a single screen press. I don't think Remix will in either mode.

---

### Post by LewRockwell on 2009-07-10
Acer Aspire One AOA-150-1864 with the Dell mini-wlan 1390 card

Report:

Working fine triple-booting XP Professional SP3, Ubuntu 9.04 Jaunty(full version), Puppy Linux 4.2.1, and with five more logical partitions for five more *nix distros!

.

---

