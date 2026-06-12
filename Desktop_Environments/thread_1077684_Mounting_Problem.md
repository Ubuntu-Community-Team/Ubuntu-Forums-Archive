---
title: "Mounting Problem"
date: 2009-02-22
forum: Desktop Environments
---

### Post by MasterNetra on 2009-02-22
Whenever i load a CD into my Drive it says it cannot mount it because i have to be the Superuser (root i assume)...how do i fix this? I'm sure I'm to blame for this when trying to do things to help ensure my system is secure...but not sure at this point what i did...(Although I'm guessing it has to do with some file permission changes but I am not sure what areas deal with the cd mounting..)

---

### Post by deepclutch on 2009-02-22
this is the line ,I have in my Intrepid /etc/fstab:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
try "gksudo gedit /etc/fstab" and edit accordingly;not exactly.

---

### Post by taurus on 2009-02-22
Look at your /etc/fstab to see what does it say about an entry for your CD/DVD.  

```
cat /etc/fstab
```
Did you change permissions of files/directories?

---

### Post by MasterNetra on 2009-02-23
It says...
> 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=85bf8905-8261-4fc1-82bd-e383e8cc048f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=852c6661-8624-4fd5-baf0-a80ec75d53d2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


---

### Post by taurus on 2009-02-23
What's the output of this command?

```
id
```

---

### Post by MasterNetra on 2009-02-24
> **taurus said:**
> What's the output of this command?

```
id
```

```

uid=1002(delta86) gid=1001(local) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(scanner),106(fuse),108(lpadmin),123(admin),124(sambashare),1001(local)

```

---

### Post by deepclutch on 2009-02-24
Go to menu System >Admin>UsersandGroups. press unlock and give your login password,press enter.:D .
OK.now you select the username from the list.then click on properties.from there browse to Account Privilages.tick on all relevent ones including "Use CD-rom drives".exit.
--
now ,try to mount a cd/dvd.reply back.
also ,if above doesnot worked ,do provide the output of below command:
```
ls -l /dev/dvd
```
and:
do this on terminal:
```
chmod +s /bin/mount
```
then try again.

---

### Post by MasterNetra on 2009-02-24
> **deepclutch said:**
> Go to menu System >Admin>UsersandGroups. press unlock and give your login password,press enter.:D .
OK.now you select the username from the list.then click on properties.from there browse to Account Privilages.tick on all relevent ones including "Use CD-rom drives".exit.
--
now ,try to mount a cd/dvd.reply back.
also ,if above doesnot worked ,do provide the output of below command:
```
ls -l /dev/dvd
```
and:
do this on terminal:
```
chmod +s /bin/mount
```
then try again.

None of it worked but this is the output.

```

**CENSORED**:~$ ls -l /dev/dvd
lrwxrwxrwx 1 root root 4 2009-02-20 23:13 /dev/dvd -> scd0

```

---

### Post by deepclutch on 2009-02-24
I guess is it can be due to some HAL issue.before inserting dvd/cd into your drive ,can you do this:
```
sudo /etc/init.d/dbus stop 
```
and then:
```
sudo /etc/init.d/dbus restart
```

THEN - insert a cd/dvd and close the tray.wait for few seconds.now ,open the Nautilus File Manager.Look at the LHS side ,where your dvd drive will also be listed.click once on the icon.It will mount most probably.for unmounting ,press on the "eject icon" shown on the same option.

---

### Post by MasterNetra on 2009-02-24
> **deepclutch said:**
> I guess is it can be due to some HAL issue.before inserting dvd/cd into your drive ,can you do this:
```
sudo /etc/init.d/dbus stop 
```
and then:
```
sudo /etc/init.d/dbus restart
```

THEN - insert a cd/dvd and close the tray.wait for few seconds.now ,open the Nautilus File Manager.Look at the LHS side ,where your dvd drive will also be listed.click once on the icon.It will mount most probably.for unmounting ,press on the "eject icon" shown on the same option.

Nope Still get a error message claiming you must be the superuser to mount. Although it does show up (at least CD title wise) under places menu, but it won't mount.

---

### Post by deepclutch on 2009-02-24
still ,let me see the output of below command from terminal:
```
groups
```

---

### Post by MasterNetra on 2009-02-24
> **deepclutch said:**
> still ,let me see the output of below command from terminal:
```
groups
```

```

local adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse lpadmin admin sambashare

```

---

### Post by MasterNetra on 2009-02-25
*bump* Unresolved

---

