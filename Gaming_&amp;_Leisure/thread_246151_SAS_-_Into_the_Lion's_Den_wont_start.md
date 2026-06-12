---
title: "SAS - Into the Lion's Den wont start"
date: 2006-08-28
forum: Gaming &amp; Leisure
---

### Post by chrism66 on 2006-08-28
I just installed SAS - Into the Lion's Den but it will not start. It started up and I played it some when it prompted me at the end of the install if I wanted to start the game. KNow it will not start. Any help would be greatl appreciated.

Regards,
Chris:confused:

---

### Post by Perfect Storm on 2006-08-29
Try start it up through the terminal and see if any error output shows up.

---

### Post by KillerBOB on 2006-08-29
Chris, maybe you installed with 'sudo ...' ? Then you probably have to change ownership of the ".lionsden"-folder since it is now owned by root.

Note that I haven't tried this game myself, I am just guessing this most likely is the case. Most likely the games' settings folder is named differently than ".lionsden" (notice the dot infront).

Hope this helps, otherwise post back

---

### Post by chrism66 on 2006-08-30
Yeah it has something to do with the permissions of the directory. I can get it to start in the terminal with "sudo sas" I have tried the chmod 777 -R, and to "chmod * sas" with sudo and in the root terminal and still it will not launch from the icon in the panel.

---

### Post by stuart.crouch on 2006-08-30
This is the same problem as Im having, not got a resolution for it yet, but thought I'd link the two threads.

[http://www.ubuntuforums.org/showthread.php?t=243339](http://www.ubuntuforums.org/showthread.php?t=243339)

Does anyone know what the permissions/ownerships should be in order for a mod to run without sudo?

---

