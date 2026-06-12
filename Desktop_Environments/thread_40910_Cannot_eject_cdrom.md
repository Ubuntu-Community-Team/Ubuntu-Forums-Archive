---
title: "Cannot eject cdrom"
date: 2005-06-11
forum: Desktop Environments
---

### Post by yccheok on 2005-06-11
Hi all, sometimes, I try to eject cdrom but not work. I have to restart my computer, then it only work. Can anyone tell me how to solve this problem?



yccheok@ubuntu:~$ eject cdrom
eject: unable to open `/dev/hdd'
yccheok@ubuntu:~$ sudo eject cdrom
Password:
eject: unable to open `/dev/hdd'
yccheok@ubuntu:~$


Thank you.

cheok

---

### Post by yccheok on 2005-06-11
oh my god, I cannt even eject after restart :(

---

### Post by not_yet on 2005-06-11
if its a harware issue, and you just want to get the cd out, there should be a small hole somewhere on the front of the cd / straighten out a paper clip, and use that to eject the cd manually

cheers

---

### Post by yccheok on 2005-06-11
pardon me for my annoaying message. It is a damm shame. My power cable was unpluged from the cdrom  ](*,)  

sorry guys.

---

### Post by TeeJay on 2005-06-11
[QUOTE=yccheok]pardon me for my annoaying message. It is a damm shame. My power cable was unpluged from the cdrom  ](*,)  

sorry guys.[/QUOTE]

sometimes my cd won't eject either, but if you paste this code in a terminal 

sudo umount /media/cdrom0/ -l     

 it forces it to unmount.

---

### Post by jeremy on 2005-06-11
[QUOTE=TeeJay]sometimes my cd won't eject either, but if you paste this code in a terminal 

sudo umount /media/cdrom0/ -l     

 it forces it to unmount.[/QUOTE]
 But if it isn't plugged in, even that won't help :-)

---

