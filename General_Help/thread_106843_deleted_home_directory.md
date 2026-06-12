---
title: "deleted /home directory"
date: 2005-12-21
forum: General Help
---

### Post by kruz on 2005-12-21
okay, i installed auditor on another partition
so now its
/dev/hda1=winxp
hda2=ubuntu
hda3=didnt get named lol skipped? its nothing
hda4=knoppix/auditor install
hda5= swap file

but whenever i boot to ubuntu
it automounted /dev/hda4 to /home and deleted all my profiles
and i can do anything but login in a terminal out of the login screen

any ideas, ill be happy to provide more info if necessary
any help would be greatly appreciated thanx

---

### Post by psusi on 2005-12-21
Was /home originally on that partition or is this something new?  I'm not sure what this auditor is, but it sounds like something configured that partition to be mounted as /home, weather you intended that or not.  

Unmount /home and the original files should reappear.

---

### Post by kruz on 2005-12-21
well, auditor is like a edited version of knoppix
and i used knoppix-installer to do that

but i dont want it ot mount at all
i changed fstab and mtab
and now theres just nothing in there, so i created a new account, and now thats in there, but it still wont let me login to a GUI

---

### Post by psusi on 2005-12-21
Did you unmount the partition though?  Just editing fstab only changes what will be mounted the next time you boot up.  You should never edit mtab directly, that's a file that mount uses to keep track of which filesystems it has mounted.

---

### Post by kruz on 2005-12-21
crap then what do u suggest
boot up into that limited shell failsafe, at the gnome login
and umount /dev/hda4?

---

### Post by psusi on 2005-12-21
If you already removed the /home mount line from /etc/fstab, just reboot normally.

---

### Post by kruz on 2005-12-21
it did and it still wont let me login
and i try to login with my new account i created
and it looks like its loading then just stays with a brown background and a mouse
if i use a terminal, i login to root
and startx it does the same thing

---

### Post by psusi on 2005-12-21
What does the output of df and ls /home look like?

---

### Post by kruz on 2005-12-21
let me boot back into ubuntu and get it

---

### Post by kruz on 2005-12-21
filesystem
/dev/hda2 used % 6%  mounted on /
thats df 
ls /home gives

brandon
my username

---

### Post by kruz on 2005-12-21
not sure if this helps, but if i try to login i dont get an error
just the brown background screen and my mouse

um, also there is nothing inside /home/brandon no Desktop, of course dir -a shows a couple things, but no desktop which i found wierd, any help at all, maybe if i know root is safe, so what command can i do to enable root login from login screen

---

