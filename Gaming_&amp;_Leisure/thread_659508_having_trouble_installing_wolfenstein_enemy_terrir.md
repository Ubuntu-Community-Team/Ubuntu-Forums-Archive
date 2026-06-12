---
title: "having trouble installing wolfenstein enemy terriroty"
date: 2008-01-05
forum: Gaming &amp; Leisure
---

### Post by tim018 on 2008-01-05
ok, i am somewhat kinda new to linux(i am using ubuntu 7.04) and i downloaded wolfenstein from the website and it is a .run file.  usually to install a .run file all i have to do is doulbe click on it, however, when i double click on the wolfenstein it tries to open it up in either a browser, text editor or an archive manager.  all of them come up with error.  why is it not running the installer instead? thanks for any help.  let me know if you need any other information

---

### Post by BreathEasy on 2008-01-05
Wasn't there a fourth option, Run? Click that.

It didn't run the installer automatically because it had not been set with the "executable" flag. This flag tells linux that the file can be run as a program, but since the flag wasn't set (freshly downloaded files don't have this flag set automatically), the file's purpose was ambiguous to Linux, so it suggested several options, one of them I'm sure being run.

If Run isn't there for some reason, open a terminal and type

cd Desktop
chmod +x FILENAME

where FILENAME is the full name of the wolfenstein installer program. I assume you downloaded it to the desktop, otherwise the commands won't work so well.

Once that's done, double-click the file again and it should work.

---

### Post by tim018 on 2008-01-06
cool, well that got me closer, now when i try to run it when the dialogue box comes up- run does nothing, run in terminal comes up with an error saying nvidia installer must be run as root.  i tried messing around in users and groups, but to no avail.  how do i fix this?

---

### Post by BreathEasy on 2008-01-06
> **tim018 said:**
> cool, well that got me closer, now when i try to run it when the dialogue box comes up- run does nothing, run in terminal comes up with an error saying nvidia installer must be run as root.  i tried messing around in users and groups, but to no avail.  how do i fix this?
What's the nvidia installer got to do with anything? Remember, Linux error messages are very specific, so copy & paste what is stated rather than just being broad.

What is the name of the file you're trying to run anyway?

---

### Post by red_Marvin on 2008-01-06
Are you running the installer as root? (sudo ./filename) the actual installer program might be developed by nvidia(?)

---

