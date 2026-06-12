---
title: "Unity app indicators stop responding frequently"
date: 2011-06-14
forum: Desktop Environments
---

### Post by psypher on 2011-06-14
I have a NVidia twinview multimonitor setup with a 1920x1080 LCD screen to the left and a 1600x900 laptop screen on the right. The LCD is primary and the launcher is correctly placed on the left. Every time I boot up my indicator applets on the panel on the primary monitor don't work. You cannot click or right click on them. The indicator applets on the right screen (laptop) works, sort of. The system tray is not present there so before rebooting unity I have no access to apps like skype. Also the indicator applets are places randomly in the wrong location, being mis-aligned beyond the right edge of the screen. So for instance I will not be able to see the shutdown button, or the me-menu. I have seen it so bad that half of the applets are not visible at all. Yet applications do not go off the edge and maximise properly as they should. Just the panel is a problem.

To fix this problem I wrote a simple, bash script called rebunity:

unity --replace &

Sometimes running it once works, sometime I have to run it several times and sometimes you just HAVE to restart GDM. Eventually I can access my primary monitor applets and everything is aligned and sometime the applets work yet the secondary right monitor is still not aligned correctly. So it just looks ugly yet I can work on primary.

This happens everyday and is very annoying and time wasting. 

I now realise the app indicators stop working on my netbook as well, which I have not setup for multimonitor. They stop working on my laptop as well, even with a single monitor setup. 

Please help, is there a bug for this issue or should I log a new one?

These are the kind of bugs that HAVE to be worked out by Oneiric, they are the kind of show stoppers that will make less technical users run away

---

### Post by SNo0py on 2011-08-16
I experience the same issue, even without multiple monitors.... very annoying and no solution anywhere on the web :(

---

### Post by psypher on 2011-08-16
> **SNo0py said:**
> I experience the same issue, even without multiple monitors.... very annoying and no solution anywhere on the web :(

have you allowed whitelisted apps to appear in the "system tray" like skype, cruptkeeper etc? i think this might be the problem. I have given up worrying about it for now, added a script to the launcher which lets me restart unity each time i log in. busy installing oneiric to see if it persists and then I will log a bug and hopefully it will get fixed before it goes final.

---

### Post by SNo0py on 2011-08-16
Thanks for the quick reply... two comments:

1) why should I worry about whitelisting anything? I just want to use apps like I did in the old Gnome shell and icons to show up there and be clickable....

2) none of the default Unity icons (Time, Login/Logout, WiFi etc) are clickable, so I cannot even log out....

---

### Post by psypher on 2011-11-14
This issue has been solved for me now in Natty and Oneiric. Must have been by updates as I did nothing myself.

---

