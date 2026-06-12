---
title: "Sudden 10.04.2 boot/login problem"
date: 2011-07-05
forum: Desktop Environments
---

### Post by UtahBud on 2011-07-05
Hi there,
I've been running 10.04 LTS (loaded using Wubi alongside Win 7 Home Premium) since late last year, with minimal problems and have thoroughly enjoyed it. 
 
However: Within the past month or so soon after logging in I've been receiving a "Low Disk Space" warning followed by the amount remaining.  First 872.6 Mb (or so) lowering slowing and sporadically to just under 400Mb.

I gained some space by removing photos and music but the space loss continued.  Saturday,  the amount remaining was 315.2 at log-in  and within minutes, while I was just reading a small text file, another warning popped up indicating I had only 36 Mb remaining.  I hadn't downloaded, updated or upgraded a thing during that session. I searched for other large files to remove and finding none I logged off and shut it down.

 Since then when I boot up to Ubuntu I get a box with the message **" Install Problem- The configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your administrator.**" It allows me to enter my password but when I hit "enter", returns me to the same screen (which is graphically different than log-in screen was when things were OK).  I tried booting to an earlier Kernel, with the same results. 

 I'm a noobie (and often Numb- I neither backed up my files nor wrote down my Firefox passwords) and don't have much experience using terminal, which I can access using safe mode. Ideally I would like to get it back up and running. However, I would settle for getting my data, especially Firefox passwords. Hope I wasn't too verbose here but wanted to include as much detail as I could. Thanks for any/all assistance. Bud

---

### Post by dirty_harry on 2011-07-05
can you boot into windows?
try accessing your wubi installation from windows:
[https://wiki.ubuntu.com/WubiGuide#How_can_I_make_a_backup_of_my_Wubi_install.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_make_a_backup_of_my_Wubi_install.3F)
[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_the_Wubi_files_from_Windows.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_the_Wubi_files_from_Windows.3F)

[B]
further information/help:[/B]
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by sanguinoso on 2011-07-05
Can you post the output of the command ```
df -h
``` here? (Run that in the terminal)

---

### Post by TDK800 on 2011-07-05
Started getting same problem after today's updates on Ubuntu 11.04

---

### Post by bcbc on 2011-07-05
I've used this tool [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) to access the root.disk from windows. (Just point it at your C:\ubuntu\disks\root.disk file - change C: if required)

Also, if you want to get it running again, I'd suggest [resizing]("http://ubuntuforums.org/showpost.php?p=10590851&postcount=2") it. (You'll likely have to do this from a live environment i.e. booting from a live CD/USB). Make sure you backup your data or the entire root.disk first.

---

