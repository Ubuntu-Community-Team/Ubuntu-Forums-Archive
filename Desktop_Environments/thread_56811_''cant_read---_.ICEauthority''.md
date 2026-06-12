---
title: "''cant read--- .ICEauthority''"
date: 2005-08-14
forum: Desktop Environments
---

### Post by dsethuraman on 2005-08-14
Hi all
I have been using ubuntu5.04 for the last 3 months or so flawlessley as my main desktop until yesterday when disaster struck. the tab in the gnome panel showed the red circle - for updates, so i click on it and it showed a list of glib etc so i click install. flash comes a message 'cant grab mouse, somebody may be evesdropping on your session'. i have a router with a builtin firewall and also run firestarter in ubuntu at startup as one of the session startup programs and the firestarter logs are always clean. i thought somebody might have breached the box and ran chkrootkit, which did not show anything of note. so i decided to change the password which i did. then i shut down the computer. later i start the computer, but now i cant get past the login screen at bootup. the moment i put the login and the password, the x session starts but it terminates straightaway and the error message is ' cant read /home/--/.ICEauthority. even the failsafe gnome does not proceed beyond this. i can however log on to the terminal. that atleast enabled me to create a new user id and password from which i can now use the box, but is there any way to salvage my usual login??  the file browser does show the offending file with the suffix 'unknown,.
Many thanks.

---

### Post by Spudgun on 2005-08-14
Who owns the .ICEauthority file?

---

### Post by Newk on 2005-08-14
Try removing the .ICEauthority file in question using sudo, either from the text login or in X as the new user.. It worked for me.

---

### Post by dsethuraman on 2005-08-14
thanks for the answer. i managed to fix it with the command

sudo chown username /home/username/.ICEauthority
borrowed from here:
[http://forums.scotsnewsletter.com/lofiversion/index.php/t12771.html](http://forums.scotsnewsletter.com/lofiversion/index.php/t12771.html)

anybody on the cant grab mouse stuff? is it a serious security breach or just nothing?
many thanks.

---

### Post by cwaldbieser on 2005-08-14
[QUOTE=dsethuraman]thanks for the answer. i managed to fix it with the command

sudo chown username /home/username/.ICEauthority
borrowed from here:
[http://forums.scotsnewsletter.com/lofiversion/index.php/t12771.html](http://forums.scotsnewsletter.com/lofiversion/index.php/t12771.html)

anybody on the cant grab mouse stuff? is it a serious security breach or just nothing?
many thanks.[/QUOTE]
That happened to someone else not too long ago-- I am pretty sure that it is not an attempt to take over you PC.

---

