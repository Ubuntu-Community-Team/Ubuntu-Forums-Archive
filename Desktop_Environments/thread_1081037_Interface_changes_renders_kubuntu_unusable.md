---
title: "Interface changes renders kubuntu unusable"
date: 2009-02-26
forum: Desktop Environments
---

### Post by rohan_vd on 2009-02-26
hello everyone,

i am a newbie to the entire linux experience. i installed kubuntu last night. while trying to get the desktop appearance right i have managed to make it completely unusable. last thing i remember is going through some menu which sharpens the desktop, clicking on fade options and something to do with trilinear filtering (apologize for the lack of knowledge, i really don't know how to get along in kubuntu).

now every time i start kubuntu the entire interface is messed up. if i focus on anything, stuff opens up in some different region of the screen. thus i'm unable to go beyond the k-menu or open any other window. is there a way to reset the entire interface? please help!!

---

### Post by jacksaff on 2009-02-26
Rename the .kde folder in your home directory to something else (don't delete it, you might want it back!). Kde will write itself a new one when you log back in, using default values. You'll lose your kde app's config so if you have a lot of that you might want to wait for someone to give a more elegant solution...

---

### Post by rohan_vd on 2009-02-26
thanks, for the reply and i got it working again :)

i restarted kubuntu in recovery mode.. in that i chose the x-server option and logged back in, everything was back to normal, just the way before i had messed it up

---

### Post by Name change on 2009-02-26
In future be more careful and instead of renaming your whole .kde directory
just delete the usual "suspects" .kde/share/config/ kwinrc and other kwin specific configuration files or plasmarc and other plasma files.
If that dosen't work also delete cache-"localhost"
On the end do what jacksaff advised you.

---

