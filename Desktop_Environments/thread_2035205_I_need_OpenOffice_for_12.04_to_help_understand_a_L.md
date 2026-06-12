---
title: "I need OpenOffice for 12.04 to help understand a LibreOffice bug - is this possible?"
date: 2012-07-30
forum: Desktop Environments
---

### Post by ronja112 on 2012-07-30
I read the earlier thread on possible coexistence of OpenOffice and LibreOffice (the answer was no) [http://ubuntuforums.org/showthread.php?t=1924823](http://ubuntuforums.org/showthread.php?t=1924823) and the wiki page [https://wiki.ubuntu.com/LibreOffice](https://wiki.ubuntu.com/LibreOffice) (the answer was still no, also after 12.04 was added to that page).

However, I would really, really want to help with further analyzing this LibreOffice bug [https://bugs.freedesktop.org/show_bug.cgi?id=51121](https://bugs.freedesktop.org/show_bug.cgi?id=51121) *"Documents produced by LO 3.5.x and 3.4.x fail to open correctly when sent through Outlook Web Access; issue not existing in AOO or OOo3.3.The document cannot be open, but if unzipped and zipped, then it open correctly."*, reported 15th June. Reason: the customer project that I am currently working on requires that I use their OWA, the problem described in the bug report has manifested there, and I have Ubuntu 12.04 at home, where it would be tolerably safe to test installing OO & LibO side by side, if that can be done. There are plenty of *n*x users in the customer organization, many of whom have LibreOffice, and it's a pain in the neck to remind everyone not to send ODT via email=OWA, but remember to always save in DOC format.

It would be easiest to create more test material if I could have both OO and LibO installed at the same time, but according to the information linked to above, it is not possible. I suspect that the impossibility of having both OO and LibO on the same Linux is one reason why further characterizing the LibO/OWA bug---not to mention solving it---has not proceeded.

Has anyone come up with a safe enough workaround so one could have both OO and LibO on 12.04, for test purposes? All (sane enough) suggestions will be received with thanks!


[i]Note that I have posted the essentially same question on the CentOS and LinuxMint forums (I use all these three Linuxes daily ATM), because IMO this LibreOffice bug really needs to be solved, and getting it solved appears to require at least a bit more tested comparison material. And comparing the behavior of OO files that have been created in Windows (where I still have OpenOffice) to LibO files that have been created in a Linux system sounds like a non-optimal approach, though in the end that's what I'll do if nothing else is possible.

I have no illusions about Micro$oft rushing to fix their OWA because of this problem. My money is on the LibreOffice team, if this one is going to get straightened out at all.[/i]

---

### Post by ajgreeny on 2012-07-30
I am uncertain if this is still possible, but it used to be possible to install beta versions of OOo alongside the older stable ones by downloading the archive of the suite DIRECT FROM ooO, and then using ```
sudo dpkg -i *.deb
``` from the folder to where you extracted all the .deb files from the archive.  The office suite, in that situation, is installed to /opt, not /usr/bin.

However, it may cause problems now due to library conflicts between OOo and LO, so you should certainly proceed with great caution if you try to do that, and be prepared to start again from scratch.

The only other possibility I can think of is to install another version of the same OS, 12.04, in a virtual machine with, for example, Virtualbox, though it will not then be in the same instance of the operating system.

---

### Post by ronja112 on 2012-07-30
> **ajgreeny said:**
> ... The only other possibility I can think of is to install another version of the same OS, 12.04, in a virtual machine with, for example, Virtualbox, though it will not then be in the same instance of the operating system.
This is a really good idea - thank you! It neatly bypasses the risks of simultaneous OO/LibO installations on the same OS instance, yet most likely produces similar enough environments for LibreOffice and OpenOffice to work in.

If nobody else comes up with anything more convincing, I'll try this out, on Friday if no extra work turns up during the week.

I wonder how much memory and disk VirtualBox will need to only run 12.04 and OO (LibO is already alive and well on the host 12.04)? I would not want to create an unnecessarily big virtual machine just for chasing one bug.

---

### Post by Hagar Delest on 2012-08-08
If you install both of them with their official packages (from their website), AOO and LibO will coexist, see: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

