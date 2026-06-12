---
title: "user accounts ubuntu 11.10 gnome"
date: 2011-10-30
forum: Desktop Environments
---

### Post by yumtum on 2011-10-30
hi i have upgraded to ubuntu 11.10 and i installed gnome cos unity sucks but i cant access any external drives. i assume this is a permissions problem and i need to allow my user account to be able to mount external drives  but how on earth is this done? in old ubuntu gnome rules it was in system settings but now that whole menu has been removed does anyone knkow how to access this or give me a command to allow mounting external drives ? thnks in advance (down with unity)

---

### Post by crdlb on 2011-10-30
Do you mean they automount and you get a permission error when accessing them, or that they fail to automount? If the latter, are you using GNOME Shell or GNOME Classic?

---

### Post by Silent Warrior on 2011-10-30
If you're using Gnome Shell, have you installed any extensions? I think there's one called Drive Menu or something - maybe you'd find that interesting.

---

### Post by yumtum on 2011-10-30
i am using gnome classic i wnat to enable privileges to my user but cant find the option my external hdd is encrypted it prompts for password but then fails with message (Not Authorized) thanks for replys i have updated my system

---

### Post by yumtum on 2011-10-30
it is not in sys settings- user accounts but i cant mount any drives not even my phone will oad up any help thanks

---

### Post by yumtum on 2011-10-31
any help?? plz this is wrecking my head almost as much as ubuntu forcing unity which is crap im gona have to chainge my os if i cant sort this problem.

---

### Post by duracella on 2011-11-02
hmm same problem, but with Gnome-shell,,, drive menu? 
mount /dev/some_ntfs_partition /mnt -t ntfs-3g -o force   (in most cases  don't you need 'force')
[URL="http://www.linuxquestions.org/questions/linux-newbie-8/trying-to-mount-an-external-ubs-drive-with-ntfs-as-read-write-665578/"]
[/URL]

---

### Post by yumtum on 2011-11-03
anyone find a solution to this prob ? cant edit user privlages to allow mounting external drives thanks

---

### Post by yumtum on 2011-11-03
> **duracella said:**
> hmm same problem, but with Gnome-shell,,, drive menu? 
mount /dev/some_ntfs_partition /mnt -t ntfs-3g -o force   (in most cases  don't you need 'force')
[URL="http://www.linuxquestions.org/questions/linux-newbie-8/trying-to-mount-an-external-ubs-drive-with-ntfs-as-read-write-665578/"]
[/URL]
my drive is ext4 encrypted and i dont realy want to mount different drives every time i plug them in thanks though unity ucks

---

