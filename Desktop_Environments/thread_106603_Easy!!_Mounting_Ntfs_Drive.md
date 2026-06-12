---
title: "Easy!! Mounting Ntfs Drive"
date: 2005-12-21
forum: Desktop Environments
---

### Post by tpnerdcore on 2005-12-21
ok i cannot take the credit for this because i know an Ubuntu expert :smile: but this method worked for me many many many times. 

1. open terminal and type "sudo nano /etc/fstab"
   -it should promp to enter a password

2.once in that file, input this code on the bottom as is
 "/dev/hd"" /media/windows ntfs rw,user,noauto,umask=000 0 0"
   *replace the "" with harddrive specification(see key)

3.save the fstab file by pressing "contol+X" and pressing Y for yes and overwriting the fstab file

4.open up ROOT TERMINAL and type "mkdir /media/windows"

5.in either root or regualar terminal and type "sudo mount a"

6. in terminal type "sudo mount /media/windows" and it should show on the desktop. 

*everytime you reboot or log off the drive will unmount. Just go to "computer" and double click on it and it will remount.

*linux cannot write to ntfs drives, only read 

*if you dont see it on your desktop, please revise
--------------------------------------------------------------
Harddrive specifiaction key--
hda=Master on your primary IDE
hdb=Slave on your primary IDE
hdc=Master on your secondary IDE
hdd=Slave on your secondary IDE

*note*if you need to mount a partition, put the partiton number after the harddrive specification.

***example--hdb2=slave on primary IDE, second partiton
--------------------------------------------------------------

please give feedback :)

anthony(tpnerdcore)

---

### Post by aysiu on 2005-12-21
Read the fourth link of my sig--it's much better, and I can take credit for it... because I wrote it!

---

### Post by tpnerdcore on 2005-12-21
i wouldnt say much better, but its nice;)

---

### Post by toya on 2005-12-21
hmm my friend suggested to me to use 222 for umask
what is the difference?

---

### Post by aysiu on 2005-12-21
[QUOTE=toya]hmm my friend suggested to me to use 222 for umask
what is the difference?[/QUOTE] NTFS should be umask=0222 to make it read-only, as it should be in Linux, if you don't want to corrupt the partition.

---

### Post by canadianwriterman on 2005-12-21
I agree with aysiu that adding this line to fstab is a better solution:

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

That way, your Windows partition mounts automatically on boot.

---

### Post by tpnerdcore on 2005-12-21
sorry about that, i was mistaken!!! everybody its "/dev/hd"" /media/windows ntfs rw,user,noauto,umask=0222 0 0"

all apologies. Even though 000 0 0 works, 0222 0 0 is safer.

anthony(tpnerdcore)

---

