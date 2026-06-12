---
title: "Desktop icons moves after remote login"
date: 2011-01-22
forum: Desktop Environments
---

### Post by kfleten on 2011-01-22
I have a terminal server environment, where the users normaly access their gnome desktop on a 24" LCD monitor. The users of course place their desktop icons all over the desktop.

The users can log into the terminal server remote as well, by using their laptops with client software like x2go-client. Some laptops only have 12" display. When they open a remote session, all desktop icons pulls togheter on the smaller desktop. 
When the users get back to their 24" displays at the office, the icons are still pulled togheter at the center of the screen, and have to be reorganized.

Is there a way to avoid this ?

---

### Post by Krytarik on 2011-01-22
I don't think that one can avoid this, it's just the same as switching to a lower screen resolution locally and then back again.

---

### Post by kfleten on 2011-01-23
I guess that means the users have to use the same resolution on their remote desktop as they use at the LTSP session at the Office.

But what resolution does the 24" LTSP client use ? There is no special settings in Lts.conf. It uses the "default", but what is that ? I only have remote access to the server, and can not start a LTSP session from where I am. Can I see wich resolution the users have used in any log file ?

---

### Post by Krytarik on 2011-01-23
I don't know if that applies to remote sessions also, but if I change the screen resolution in my local session, the applied mode is logged in /var/log/Xorg.0.log .

---

### Post by kfleten on 2011-01-25
I could not find the resolution of the LTSP clients in /var/log/Xorg.0.log, so went to visit the users.

We have solved the problem by arranging the icons at the smallest resolution (the remote desktop).

---

