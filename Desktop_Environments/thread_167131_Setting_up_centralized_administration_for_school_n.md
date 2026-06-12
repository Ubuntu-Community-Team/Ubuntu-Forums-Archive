---
title: "Setting up centralized administration for school network"
date: 2006-04-27
forum: Desktop Environments
---

### Post by xXdaveXx on 2006-04-27
I am in the process of converting somewhat disorganized network of 10 Windows-powered computers over to a more organized Ubuntu network. The old system was just a line of unconfigured Windows 98-XP machines, which were loaded with spyware/viruses and barley worked. Because getting anything from the school, mouse or Windows Server 2003 licence, is either impossible or takes a year or so to process, I turned to the slighly easier solution: wipe them all with Ubuntu and network them into something workable. 

The network is for a journalism class, which needs really only four programs: Adobe InDesign CS2, Adobe Photoshop CS2, a word processor (OpenOffice), and a web browser (Firefox). All are either avalible for Linux or runnable through Wine, although I'm still testing. 

I would like to be able to network these computers with not only shared directories, but a login system in which all the systems have the same table of users. Furthermore, this use system should be able to apply appropriate user permissions (user A cannot change any operating system settings and gets access to this share, user B can change settings and get access to this and this share, etc). 

Probally the easiest way to go, although I'm not an expert in this area, would be to make all appropriate files and settings automatically load off a central server on boot. When the computer is rebooted, any changes to that system itself is wiped and the new copies are once again loaded off a central server. This means only a single computer (the server) would have to be modified, and once all the computers are rebooted, that change is distributed and the computer's own settings files are overwritten. 

This is a system a friend suggested, if you know better and/or how I would go about accomplishing the above it would really help.

---

### Post by louis_nichols on 2006-04-28
Is [this]("https://wiki.ubuntu.com/ThinClientHowto") what you are thinking about?

---

### Post by xXdaveXx on 2006-04-28
Yes, thats exactly what I was thinking about! Thanks!

---

### Post by louis_nichols on 2006-04-28
Wellcome! As you might have read already, edubuntu could be what you're looking for, rather than (K)(X)Ubuntu.

---

### Post by xXdaveXx on 2006-04-28
[QUOTE=louis_nichols]Wellcome! As you might have read already, edubuntu could be what you're looking for, rather than (K)(X)Ubuntu.[/QUOTE]

Edubuntu would appear to be aimed at younger children, while the users of these computers will be of grades 7-12th, mostly 10th or above. The tools seen in Edubuntu are largley unneccecary for the age group.

---

