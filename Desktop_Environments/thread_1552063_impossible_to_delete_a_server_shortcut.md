---
title: "impossible to delete a server shortcut"
date: 2010-08-13
forum: Desktop Environments
---

### Post by jeanmarc on 2010-08-13
hello,
on lucid 10, i have a nas server shortcut which does not function. it appears in the left column of nautilus and in the menu/shortcuts.
i don't succeed to delete it. when right clicking, i get a window : "cannot be mounted", but no line for suppression.
in gksudo nautilus, this shortcut does not appear because it is not mounted.
in editing the shortcuts, it does not appear.
have you a solution?
thank you ++

---

### Post by sydbat on 2010-08-13
> **jeanmarc said:**
> hello,
on lucid 10, i have a nas server shortcut which does not function. it appears in the left column of nautilus and in the menu/shortcuts.
i don't succeed to delete it. when right clicking, i get a window : "cannot be mounted", but no line for suppression.
in gksudo nautilus, this shortcut does not appear because it is not mounted.
in editing the shortcuts, it does not appear.
have you a solution?
thank you ++While in Nautilus, go to "Bookmarks" and then "Edit Bookmarks". This should allow you to remove unwanted references to the nas server.

---

### Post by jeanmarc on 2010-08-14
thank you, sydbat, for your kind advice. unfortunately, the "edit bookmarks" window allows to change only the lower part of the left nautilus column, but not the content of the higher part, which includes the file system files and server connections. another suggestion?

---

### Post by s990we on 2010-08-14
> **jeanmarc said:**
> thank you, sydbat, for your kind advice. unfortunately, the "edit bookmarks" window allows to change only the lower part of the left nautilus column, but not the content of the higher part, which includes the file system files and server connections. another suggestion?

If you added you nas to /etc/fstab it will show up in nautilus, I had similar problems when trying to mount ntfs partitions with the wrong parameters in fstab.

---

### Post by jeanmarc on 2010-08-14
> **s990we said:**
> If you added you nas to /etc/fstab it will show up in nautilus, I had similar problems when trying to mount ntfs partitions with the wrong parameters in fstab.

thank you, s990we, for your feedback.

here is my fstab file:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ea7a8dc0-c5a3-4b87-b2af-3001e40f0808 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=92756ae6-e45b-48af-8f77-88b206a16119 /home           ext4    defaults        0       2
# /temp was on /dev/sda7 during installation
UUID=efd9b056-066e-4254-a1cd-8445a7b97912 /temp           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=955dd070-eee8-4a8c-a9c5-16662a043275 none            swap    sw              0       0

# Entry for minilink/share
//192.168.0.199/share/ /media/minilink  cifs user,rw,uid=1000,gid=1000,file_mode=0640,dir_mode=0750,iocharset=utf8,user=xxxxx,pass=xxxxxx 0 0
```the last line allows to create an icon which works well, for mounting the nas.

i tried to delete the first line /dev/sda1 which has a "errors-remount" mention, but it does not help.

i have still two icons/lines in nautilus and shortcuts menu with the same nas name: one which works well, the second one which does not work and that i cannot delete.

suggestion?

---

### Post by s990we on 2010-08-14
> **jeanmarc said:**
> thank you, s990we, for your feedback.

here is my fstab file:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ea7a8dc0-c5a3-4b87-b2af-3001e40f0808 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=92756ae6-e45b-48af-8f77-88b206a16119 /home           ext4    defaults        0       2
# /temp was on /dev/sda7 during installation
UUID=efd9b056-066e-4254-a1cd-8445a7b97912 /temp           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=955dd070-eee8-4a8c-a9c5-16662a043275 none            swap    sw              0       0

# Entry for minilink/share
//192.168.0.199/share/ /media/minilink  cifs user,rw,uid=1000,gid=1000,file_mode=0640,dir_mode=0750,iocharset=utf8,user=xxxxx,pass=xxxxxx 0 0
```the last line allows to create an icon which works well, for mounting the nas.

i tried to delete the first line /dev/sda1 which has a "errors-remount" mention, but it does not help.

i have still two icons/lines in nautilus and shortcuts menu with the same nas name: one which works well, the second one which does not work and that i cannot delete.

suggestion?
Only thing i can think of is to comment out you nas line from fstab and check if one or both shortcuts disappears from nautilus. 
if they do verify that its the right username/password etc for you nas...

---

### Post by jeanmarc on 2010-08-14
> **s990we said:**
> Only thing i can think of is to comment out you nas line from fstab and check if one or both shortcuts disappears from nautilus. 
if they do verify that its the right username/password etc for you nas...

thank you for the suggestion. i will check and let you know.

---

### Post by jeanmarc on 2010-08-15
> **s990we said:**
> Only thing i can think of is to comment out you nas line from fstab and check if one or both shortcuts disappears from nautilus. 
if they do verify that its the right username/password etc for you nas...

hello,
when i suppress the two last lines of the fstab file, both nas shortcuts disappear.
when i introduce them again, both shortcuts are there again.
the username and password are correct.
is there something that i could change in this command for mounting the nas server?

---

### Post by s990we on 2010-08-16
> **jeanmarc said:**
> hello,
when i suppress the two last lines of the fstab file, both nas shortcuts disappear.
when i introduce them again, both shortcuts are there again.
the username and password are correct.
is there something that i could change in this command for mounting the nas server?

Check [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) 

It seams to have everything you need :)
Good luck

---

### Post by jeanmarc on 2010-08-16
thank you for your interesting link. by the mean time, with the help of the french ubuntu forum, i found the solution.

my mounting line in fstab was written as :
```
//192.168.0.199/share/
```

it should be written without /:
```
//192.168.0.199/share
```

that's it. like this, the wrong icon does not appear anymore.

thank you for your kind help and attention ++

---

