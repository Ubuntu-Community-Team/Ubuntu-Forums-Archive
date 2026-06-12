---
title: "How do I pass parameters to a program started by clicking the icon?"
date: 2024-04-29
forum: Desktop Environments
---

### Post by Just4Fun20 on 2024-04-29
Searching says to modify the .desktop file, but I can't find it.  

Background... more details - I installed a clean Ubuntu Desktop 24.04 in a Hyper-V session.  It worked great.  I installed all of my standard applications with few problems.  The only piece I'm stumbling on now is SABNZBD.  For downloaded files they use "/var/snap/sabnzbd/common".  I prefer "/home/USER/Downloads".  The problem is that they use a "Default Base Folder" so I can't navigate to /home when specifying the "complete" folder (or the "download" folder for placing .NZB files).  Searching SABNZBD forums says it's simple... you simply use the /f parameter, which will provide a new location for the SABNZBD.ini file which will become the new Default Base Folder.  

The problem is that I start SABNZBD by clicking the icon, which I've pinned to the dash.  Supposedly I can change those parameters by modifying the .desktop file, but I can't find that.  

So, back to the original (short) question... In Ubuntu 24.04, how do I pass parameters to a program started by clicking the icon?

Thanks in advance for any pushes in the right direction.

---

### Post by Holger_Gehrke on 2024-04-29
'.desktop' is not one file, it's the extension for files that hold information about starting a program from the GUI, one '*.desktop' file per program. For programs installed through 'apt' - meaning package files with the extension .deb - these can mostly be found in /usr/share/applications/. But since you probably installed sabnzb as a snap - a newer, different package format which tries to lock programs down to minimize the damage a misbehaving or malicious program can do - the .desktop file for the program is probably somewhere in /var/lib/snapd/desktop. Changing that file is probably futile, I think snapd - the management process for snaps - will overwrite any changes you make at the next update at the latest, if not at the next reboot.

What you should do is copy the *.desktop file for sabnzb to your personal directory for desktop files ~/.local/share/applications/ (~ is a shorthand for your home directory). *.desktop files in that location override the system wide ones on a per user base. Edit that copy to make any changes you want. If you're unsure about the format of .desktop files, look up the specification on [freedesktop.org]("https://specifications.freedesktop.org/desktop-entry-spec/latest/").

Holger

---

### Post by Just4Fun20 on 2024-04-29
Thank you Holger. 

Very nice writeup of the desktop (settings) workings.  

I've solved my problem.  

Have a great day.

---

### Post by ActionParsnip on 2024-04-30
Please mark as solved

---

### Post by TheFu on 2024-04-30
> **ActionParsnip said:**
> Please mark as solved

+1!    Yes please!  Don't make people waste time for already SOLVED threads.  "Thread Tools" button, near the top of the page.  It also helps others with the same issue find possible answers faster. 

Ah --- seems it was marked SOLVED already. Sorry.

---

### Post by MAFoElffen on 2024-05-01
An aside... I was thinking that if you point a .desktop exec line to a script, then someone could make it possible to choose various startup options, by user choice. or just create different distinct .desktop files with different startup options, so that you aren't bothered each time 'having' to make a choice.

There are multiple possibles there with that.

---

