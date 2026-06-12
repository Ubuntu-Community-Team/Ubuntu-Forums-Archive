---
title: "Cannot burn any kind of CDs"
date: 2009-05-30
forum: General Help
---

### Post by OsamaK on 2009-05-30
Hello, I am trying to burn a data cd using k3b 1.0.5 (I had same problems with Brasero, but I prefer k3b debug information over Brasero's) under Ubuntu 9.04. I tried many ways to fix this, and finally I decided to have a fresh start: 
[LIST=1]
[*] Completely removed k3b, cdrdao and wodim and reinstall them.
[*] Open k3b, add some files,  insert an empty CD, select "Project - Burn" with "Auto" speed and "Auto" writing mode and start burning.
[*] Before writing anything it shows *"Cdrecord has no permission to open the device"*.
[*] I found this [topic]("http://ubuntuforums.org/showthread.php?t=1062163") and write the command "sudo chmod +s /usr/bin/wodim"
[*] The error *"cdrecord returned an unknown error (code 254)"* showed.
[*] I googled for that, but all found reports were on burning audio cds and no answers were found.
[/LIST]
I had this problem since while, I'll be very glad is somebody could help me fix this problem.

---

### Post by mrog on 2009-05-30
In system/administration/users and groups, does your user have the "User privilege" to "Use CD-ROM drives"?

If you do "sudo k3b" does it work?

---

### Post by OsamaK on 2009-05-31
Yeah. SomehowI could burn three cds a data cd and two ISO image of gNewSense and Ubuntu. How to do it without root access?

---

