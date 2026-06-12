---
title: "mntent:no final new line /etc/fstab"
date: 2005-05-12
forum: Desktop Environments
---

### Post by elfwind on 2005-05-12
hy all,this is my first post,i dowloaded ubunto +kubunto about 3 days ago after trying a few different distro's and to be honest i love it,had a few probs at first but after reading the threads on the forum i got most things ironed out,i have one annoying problem however,when i log out and shut down, halfway through the kill system  a line reads" warning mntent:no final new line at the end of /etc/fstab.
and another prob,sound is ok using kde desktop but when i use gnome and start an app or anything a box pops up saying sound is bieng used by something else ,reverting to null sound driver or something like that.

---

### Post by Alexander Kirillov on 2005-05-12
[QUOTE=elfwind]hy all,this is my first post,i dowloaded ubunto +kubunto about 3 days ago after trying a few different distro's and to be honest i love it,had a few probs at first but after reading the threads on the forum i got most things ironed out,i have one annoying problem however,when i log out and shut down, halfway through the kill system  a line reads" warning mntent:no final new line at the end of /etc/fstab.
[/QUOTE]
You can safely ignore this. But if it annoys you, edit the file manually (using sudo gedit /etc/fstab), put the cursor at the very end of last line, and press enter. Now save the file and reboot. 
>  
and another prob,sound is ok using kde desktop but when i use gnome and start an app or anything a box pops up saying sound is bieng used by something else ,reverting to null sound driver or something like that.
See [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) or search these forums - it has been discussed a number of times.

---

### Post by elfwind on 2005-05-12
thanx for your help,all working ok now :)

---

