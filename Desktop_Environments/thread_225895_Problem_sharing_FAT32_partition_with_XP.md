---
title: "Problem sharing FAT32 partition with XP"
date: 2006-07-30
forum: Desktop Environments
---

### Post by boyprodigy on 2006-07-30
For some odd reason ubuntu will not write to the FAT32 partition I've made to share with LAMEdows XP unless I'm logged in as root. I have tried to give permission to my user account but ubuntu will not have it. It unchecks the write box right after I click it. I've even tried giving ownership to my user account and it says it can't transfer the ownership.

Any ideas on how to fix this?

XP can read/write on the drive just fine.

---

### Post by x64Jimbo on 2006-07-30
What about changing the way the drive is mounted in your /etc/fstab?
There's a permissions mask you can tweak to allow your user write permissions on that drive.

---

### Post by mephisto56 on 2006-07-30
do you mean setting umask to 777 instead of 007?

---

### Post by x64Jimbo on 2006-07-30
Actually, no. umask is opposite of chmod. To grant more permissions, you have to go lower. In this case, you could change that last 7 to a zero and see if that fixes it.

---

### Post by mephisto56 on 2006-07-30
For me the problem is solved with that. Everyone gets read/write access now, ownership stays with root.

---

### Post by x64Jimbo on 2006-07-30
Glad I could help.

---

### Post by boyprodigy on 2006-07-30
I'm sorry, but I'm still lost. It's day 3 of using linux for me :p 

I've taken some screenshots to show you what I've tried

Screenshot1 is showing the drive is mounted,
Screenshot2 is showing that I can't write to it, only read (tried to change it to read/write under root, but it automatictly unchecks it whenever I check it)
Screenshot3 is showing me trying to give ownership to my account (jon) but it not letting me.

---

### Post by x64Jimbo on 2006-07-30
Did you change the settings in /etc/fstab? You really should try that. Just make the umask on that drive 0000 and reboot. See if that helps

---

### Post by boyprodigy on 2006-07-30
for some reason the drive isn't even in etc/fstab. Should I just make a new line for it?



**EDIT:**if i should add it should it look like this

/dev/hda4       /home/Shared            vfat    rw              0       0

---

### Post by mephisto56 on 2006-07-30
Mine looks like this:

/dev/hda2  /media/hda2 vfat defaults,utf8,umask=000,gid=46 0  1

---

### Post by boyprodigy on 2006-07-30
Thanks mephisto56, I just copied the defaults,utf8,umask=000,gid=46 and it's working super fine.

---

### Post by mephisto56 on 2006-07-30
Thank x64Jimbo for that. ;-)

---

