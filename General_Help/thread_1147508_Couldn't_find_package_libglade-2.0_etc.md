---
title: "Couldn't find package libglade-2.0 etc"
date: 2009-05-03
forum: General Help
---

### Post by Kitsune23 on 2009-05-03
Hello,
 
I am a novice Ubuntu user. I use a dell netbook that is powered by Ubuntu. Everything went smoothly for about a month until today.
I couldnt get the computer to start up and had this error message:
 
"[FONT=Times New Roman][SIZE=3]Ubuntu your session lasted less than 10 seconds. gdmflexiserver: error while loading shared libraries: libglade-2.0.so.0: cannot open shared object file: No such file"[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]I tried: sudo apt-get install libglade2.0 and that did not work. Got a message stating "couldn't find package'[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Then I tried $ sudo find / -name "lib_name"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]did not work either. Unless i used a wrong syntax.[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Please help me... I have work saved on that device that I need to access before a presentation tomorrow and am prevented from doing so until this issue is resolved :-([/SIZE][/FONT]

[FONT=Times New Roman][SIZE=3]Thanks...[/SIZE][/FONT]

---

### Post by Kitsune23 on 2009-05-03
Update:
 
So, in failsafe terminal, I typed:
sudo apt-get install libglade 2-0

Then I get:

Reading package lists... done
Building dependency tree... done
libglade 2-0 is already the newest version.
libglade 2-0 set to manually installed
The following packages were automatically installed are are no longer
required: dhcdbd libisc32
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I tried setting libglade to automatic install but the system didn't allow me.
I am at wits end :-( I really to access that file.

Is there a way to log in to the computer from the failsafe terminal or
is it only for solving problems?

Any help/tips you can share would be great :/

---

