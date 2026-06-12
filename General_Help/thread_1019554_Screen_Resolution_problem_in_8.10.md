---
title: "Screen Resolution problem in 8.10"
date: 2008-12-23
forum: General Help
---

### Post by jmetric on 2008-12-23
This is a self-created problem that I can't figure out how to get out of.

I wasn't happy with the screen resolution as it was so I tried a different resolution, which was worse.  Particularly so because it is so large I cannot access the buttons at the bottom of the System>Preferences>Screen Resolution page to change it back to the previous setting.

How do I resolve this?  

Thanks for any and all help.

---

### Post by pgdave on 2008-12-23
Hit Alt-F7  (move window). then use the cursor keys to move it up so that you can access the buttons

HTH

---

### Post by Titan8990 on 2008-12-23
Hit CTRL+ALT+F1

Log in to the terminal there.


Use the following command to reconfigure your graphics settings:


sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start


If there is an entry that you don't know about, just hit enter to accept it's current setting.


You still might have to edit /etc/X11/xorg.conf manually.


Let me know if you are still having issues after re-configuring xserver.

---

### Post by jmetric on 2008-12-23
damn...  it's so easy when you know!   thanks, worked like a charm!

---

### Post by Titan8990 on 2008-12-23
Not sure what you did but thats good to hear. Don't forget to mark your thread as solved.

---

