---
title: "Plasma Shell, Segmentation fault on start-up"
date: 2012-09-21
forum: Desktop Environments
---

### Post by Mookawaka on 2012-09-21
I am using KUBUNTU 12.04 LTS.

More often than is comfortable for me, I am receiving a critical error message when my desktop boots of a "Segmentation Fault (11)" with plasma-desktop.

Normally this just means an extra long start-up.  Occasionally I must re-boot.

This problem does not occur with the netbook variant on my other computer.

I have a vague suspicion that this may have to do with maintaining a rather old /home folder rolling through various UBUNTU releases that has irrelevant saved settings floating around in there.  The same happens rarely with my wife's work computer that has a similar setup and home folder history.

I have been searching around cyberspace for a solution to no avail, though some have stated that segmentation faults are a scary bad thing.

---

### Post by Mookawaka on 2012-09-22
Any KDE/Ubuntu users floating around these forums anymore? :KS

bump.

---

### Post by bra|10n on 2012-09-22
Not using Bespin by any chance?

---

### Post by NormanFLinux on 2012-09-23
I get occasionally it on my netbook.

Fortunately its a rare occurrence. Its one those bugs that never gets fixed. I'm running the latest 4.9.1 KDE Plasma Desktop.

---

### Post by Mookawaka on 2012-09-23
bra10n
No I am not using Bespin.

NormanFLinux
I have also read that this problem appears to go back at least to Kubuntu 11.10.  Do you know if this segmentation fault problem is a registered bug?

---

### Post by bra|10n on 2012-09-23
> **Mookawaka said:**
> I am using KUBUNTU 12.04 LTS.

More often than is comfortable for me, I am receiving a critical error message when my desktop boots of a "Segmentation Fault (11)" with plasma-desktop.

Then the only consistant error on startup I recall is KNetAttach crashing...

You might take note of the package responsible the next time it happens and search launchpad for reported bugs.

---

### Post by Mookawaka on 2012-09-24
The exact error meesage reads as:

Details:
Executable: plasma-desktop PID: 1844 Signal: Segmentation fault (11)


In a second error dialogue after reboot:

ExecutablePath
/usr/bin/plasma-desktop

---

### Post by bra|10n on 2012-09-24
You might try either of these,
1. Create a new user and login with this new account to see if the same error message appears.
2. Re-name (or delete)~/.kde4 folder, and reboot to your user account. (deleting will result in all customisations > to default; settings, themes etc

---

### Post by Mookawaka on 2012-09-26
There is a second account on this computer with a relatively simple desktop setup consisting of only one *activity*.  I have not been able to reproduce the Segmentation fault crash with that account.

I guess this means there is a problem with a widget or activity that I am using on my desktop account? Or maybe something got corrupted while trying out mocules and getting the desktop setup?

I am not using any widgets or activities that do not come pre-packaged with Kubuntu.

---

### Post by bra|10n on 2012-09-26
So option 2 I suggested above is a solution. Try just renaming ~/.kde4 first though.
As long as you don't mind having to reset your themes, etc

---

### Post by kio_http on 2012-09-27
Do you have any weird widgets that you installed? What is the last change that you did before this happened? Did you try updating to KDE 4.9.1 (see kubuntu.org to do that)?

What graphics card do you have?

Try turning of desktop effects in system settings and see if the issue persists.

---

### Post by Mookawaka on 2012-10-22
By setting up the KUBUNTU backports repository and updating to KDE 4.9 the segmentation faults are no longer happening.  It would appear that they ironed out some of the bugs upstream.
((SOLVED!))

kio_http, that is a very nice little kde/kubuntu optimisation guide that you have attached to your signature.  I will be using some of the tips in the near future.

Thanks also to bra|10n for helping to localise this problem.

---

### Post by linuxrev on 2013-07-01
I had a similar problem. After changing settings for a plasma widget, i.c. Worldclock, plasma started to do weird things. After restarting the computer the next day I got this error: "Executable: plasma desktop PID: 2413 Signal: segmentation fault". The screen was black, no desktop panel or systemn tray. Luckily keyboard shortcuts did work, so I could open a terminal. Fearing that I would need to fall back to the blunt 'rename .kde dir' method I tried the following, which worked.

First I made sure the process causing the trouble was really terminated:
  $ kill 2413

Then I edited the ~/.kde/share/config/plasma-desktop-appletsrc file. Because I suspected the Worldclock widget to be the villain, I looked for the [Containments] section with the line 'plugin=worldclock' in it, and simply removed this section. That did the job, because I could reboot as normal, and reinstall the worldclock thingy.

-- 
linuxrev
(LinuxMint 13 / KDE 4.8)

---

