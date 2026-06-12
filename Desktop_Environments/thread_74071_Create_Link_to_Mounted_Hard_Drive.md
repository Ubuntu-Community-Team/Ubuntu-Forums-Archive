---
title: "Create Link to Mounted Hard Drive"
date: 2005-10-10
forum: Desktop Environments
---

### Post by karuptdata on 2005-10-10
I have mounted a partition successfully and also edited my /etc/fstab to mount the directory to the desired location "/home" how do i create a link to be able to write as well as read on this partition..any help or guidance would be appreciated!

---

### Post by Leif on 2005-10-10
if it's an ext3 partition, here's my fstab entry :

/dev/hda7       /home           ext3    defaults        0       2

---

### Post by karuptdata on 2005-10-10
thats how mine is set up as well however how do i navigate to partion with say a system link or shortcut??

---

### Post by Leif on 2005-10-10
I'm not sure I understand your question. The system link is /home or ~ for your home.

---

### Post by karuptdata on 2005-10-10
[QUOTE=Leif]I'm not sure I understand your question. The system link is /home or ~ for your home.[/QUOTE]
 Correct the link in fstab is listed as /home...is that correct? I should have been more clear i would like to have a launcher on my desktop that launches the file browser for thar partition.

---

### Post by Leif on 2005-10-10
click on places, drag "home folder" to your desktop

---

### Post by karuptdata on 2005-10-11
I would like to have a launcher on my desktop that launches the file browser for thar partition. Not my home folder but the actual partition that is mounde which is dev/hda6 is that at all possible?

---

### Post by Leif on 2005-10-11
ln -s /dev/hda6 ~/Desktop/

---

