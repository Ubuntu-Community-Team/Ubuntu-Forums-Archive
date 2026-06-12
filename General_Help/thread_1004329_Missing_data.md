---
title: "Missing data"
date: 2008-12-07
forum: General Help
---

### Post by LinnetLegs on 2008-12-07
First I will like to say don't judge me by my ignorance ;) and please try to give any answers in easy to understand format.

I have installed ubuntu on my laptop yesterday mainly because I like 'messing about' to find out how things work. I had two drives - one where I stored all my data (D drive). I was sensible enough to back it all up on an external drive so I haven't lost anything.

My main problem is I cannot 'see' D drive as a separate drive so I don't know if the data has gone. 

When I installed ubuntu - does it see both drives as one or is D drive not accessible now?

I know I sound naive but I would appreciate any help/advice/information

---

### Post by adult swim on 2008-12-07
if you go to Places>Home Folder and look in the left pane, do you see anything that is labeled something like 60 GB Media?  its not going to be 60, i just used that as an example

---

### Post by LinnetLegs on 2008-12-07
no - I can see 'desktop' 'documents''examples' 'music''pictures' public' 'templates' and 'videos'

---

### Post by adult swim on 2008-12-07
go to a terminal (applications>accessories>terminal) and type in ```
sudo fdisk -lu
``` it will ask for your password, type it in and press enter.  paste the results here

---

### Post by LinnetLegs on 2008-12-07
Thanks for helping - here is the text:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb58e199

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476311184   238155561   83  Linux
/dev/sda2       476311185   488392064     6040440    5  Extended
/dev/sda5       476311248   488392064     6040408+  82  Linux swap / Solaris

---

### Post by adult swim on 2008-12-07
try going to the terminal again and entering in ```
sudo mount /dev/sda2
``` and then check out the places menu again.

---

### Post by LinnetLegs on 2008-12-07
It says:

mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab

---

### Post by adult swim on 2008-12-07
ive never really messed around with fstab or mtab so i dont really feel comfortable giving you directions on how to fix that.  however, i have a suspicion that instead of having two hard drives you have one hard drive that is split into two paritions.  to see if this is the case you'll need to run a couple of commands.  you can enter these one by one in the terminal
```
sudo mkdir /mnt/data
sudo mount /dev/sda2 /mnt/data
```
once you have done this, go to places>home folder and then look on the left pane and select file system.  then go to the folder that is called mnt and double click it.  then double click the data folder.  if the stuff that was on your D drive is in there that means it is on the second partition.  if this is the case, im sure someone knows how to make this work alot easier with fstab.

---

### Post by LinnetLegs on 2008-12-07
OK -thanks for the help. It isn't there. I will just have to get it from the external hard drive.

I guess what you said is true, that there is one drive that is partitioned. I know the total size of the drives was 250GB and I can see that figure in the first lot of text I pasted in my reply to you.

Thanks again.

---

