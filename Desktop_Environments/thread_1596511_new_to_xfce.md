---
title: "new to xfce"
date: 2010-10-14
forum: Desktop Environments
---

### Post by jonnny_j22 on 2010-10-14
Hi all,

I just installed a base system from the mini.iso and have loaded xfce on top using slim to login there's just a couple of things I can't seem to work out:

1) how do I add a scroll bar to the terminal window? (last time I used Xfce it was there automatically) 

2) I like to keep all my data on a serperate partition, Midori can see my other partitions to save to it, but the file manager does not see the partitions to mount tthem. how do I make my other partitions visable in the side panel of partition manager and be able to mount them and read/write from/to them in the file manager window?

If atal possible, I'd like to make these changes without installing the whole Xubuntu package as this is a deliberatly minimal partition for work that only uses a terminal, browser, word/spreadsheet processor and and a mail client.

Thanks in advance guys!

---

### Post by sisco311 on 2010-10-14
[list=1]
[*]Right click on the terminal -> Preferences -> General tab -> Scrolling -> Scrollbar is: On the right side.


[*]Try installing thunar-volman.
[/list]

---

### Post by 3Miro on 2010-10-14
Not sure about the first question.

For the second one, manually edit the fstab and mount the volumes to /media/something at boot. Then manually add the shortcuts to Thunar. This will install nothing and it will work just fine.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I don't have thunar-volman and I am still able to mount internal HDD with fstab and external ones automatically.

---

