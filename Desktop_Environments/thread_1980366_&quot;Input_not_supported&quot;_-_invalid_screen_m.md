---
title: "&quot;Input not supported&quot; - invalid screen mode being set AFTER login"
date: 2012-05-15
forum: Desktop Environments
---

### Post by endian675 on 2012-05-15
I have a strange issue with Ubuntu 11.04 that's happened after moving to a different monitor.  On boot up the machine shows the logon screen correctly, in 1920x1200.  However, after I type in my password, the screen mode is changed to an invalid one - 1680x1050 - that my new monitor cannot display, but my old one could.  

However, this *only* happens with the user account that was also in use on the old monitor.  I've just created a new user ("testuser") and can log in with no "Input not supported" issues.  
The xorg.conf that I have should not be setting 1680x1050, and you can see in the Xorg.0.log that earlier on in the boot process the correct mode is being chosen.  It's only after login that the invalid 1680x1050 mode is set, and then only for this particular user.  Is there some file in that user's home directory that could be causing 

Attached is my xorg.conf, the Xorg.0.log for the successful login with the new user, and the Xorg.1.log for the failed login.  

I hope you can help, I'm tearing my hair out!

---

### Post by endian675 on 2012-05-15
I've just resolved this.  My suspicions about a rogue file were correct.  The file ~/.config/monitors.xml contained the old resolution of <width>1680</width> and <height>1050</height>.  Changing these to 1920 and 1200 allowed me to login again.

---

