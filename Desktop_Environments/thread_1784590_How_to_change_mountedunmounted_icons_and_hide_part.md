---
title: "How to change mounted/unmounted icons and hide partitions?"
date: 2011-06-17
forum: Desktop Environments
---

### Post by Rotura on 2011-06-17
Hi all! This is my first thread on these forums and English is not my native language so I expect everybody could understand me :-S I'll try my best.

I installed Xubuntu two days ago and it seems very nice. But one thing I don't like is that all my partitions appear over the desktop. I have one for random stuff (which I like to have on the desktop), and one for windows XP (**this laptop** has dual boot with it) which I would like NOT to have on the desktop.

My second problem is that mounted and unmounted partitions use the SAME icon and I'd like to have ONE icon for mounted and ANOTHER one for unmounted partitions so I could see if I have mounted partitions without having to put the mouse pinter over their icon.

_I've tried to search_ the answer to these questions over the internet and using the IRC channels for Xubuntu and XFCE without any help. The majority of google results about this talk about mounting problems, which is not the case.

One of my searchs gave me to this thread:
[http://www.linux-solved.com/post/Hide-Windows-partition-icons-on-Desktop-in-Xfce-SOLVED-71046.html](http://www.linux-solved.com/post/Hide-Windows-partition-icons-on-Desktop-in-Xfce-SOLVED-71046.html)
Which mentions this other thread:
[https://bbs.archlinux.org/viewtopic.php?pid=882105#p882105](https://bbs.archlinux.org/viewtopic.php?pid=882105#p882105)

So I tried to make a .rules file on /etc/udev/rules.d/  hiding my windows partition, and it worked, but THEN I became to have a problem with my home: when I opened the file manager I had an error saying there was a ".gvfs" and the other side was not connected/linked (I don't know is it's correct in English, in Spanish it says "*Error al mostrar la información del estado del archivo «/home/my_user/.gvfs»: El otro extremo de la conexión no está conectado.*").

This only happened on the file manager. I was able to navigate through my home without problems using a Terminal. But, at the end, I deleted that .rules file because being able to use the file manager is more important to me :-S

So, trying to me more clear, I would like to:
1.- Hide my windows partition (it could be ok if I could add a /etc/fstab making it unmountable but I would like to hide it).

2.- Make my mounted and unmounted partitions to use different icons for each state.


Thanks a lot for your help and patience, and sorry about my poor english.

---

### Post by Rotura on 2011-06-18
Can I get some help, please?  :(

---

### Post by Toz on 2011-06-18
> **Rotura said:**
> 
1.- Hide my windows partition (it could be ok if I could add a /etc/fstab making it unmountable but I would like to hide it).
The /etc/udev/rules.d/ method is the correct way to do this. I'm currently using this method and don't have the problem you mention with .gvfs - so I think it maybe something else. What is the current contents of your **~/.gvfs** and **~/.local/share/gvfs-metadata** folders?

> 2.- Make my mounted and unmounted partitions to use different icons for each state.
Have you tried changing the icon theme? Does it make a difference? I thought I came across a launchpad bug report recently about the similarity of the icons, but of course, I can't find it now. I'll post the link if I find it.

---

### Post by Morbius1 on 2011-06-18
> 1.- Hide my windows partition (it could be ok if I could add a /etc/fstab making it unmountable but I would like to hide it).Mount points in /media and /home/username result in destop icons. If those mount points are anywhere else they don't create desktop icons.

[1] If you have the ntfs partition mounted unmount it.

[2] Run the following command:
```
sudo blkid -c /dev/null
```You will get among other things lines that look like this:
> /dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" 
/dev/sdb6: LABEL="Data" UUID="f7927995-b098-42be-ada0-987857f5177a" TYPE="ext3" [3] Create a mount point so that the Windows partition is not on the desktop:
```
sudo mkdir /WinXP
```Then add a line in fstab that looks like this:
```
UUID=DA9056C19056A3B3 /WinXP ntfs defaults,uid=1000 0 0
```[4] Save fstab and in a terminal run the following command to test for errors and mount the ntfs partition at /WinXP:
```
sudo mount -a
```For the other partition where you do want an icon on the desktop - and lets say it's the ext3 p[artition from blkid:

* unmount the partition then:
```
sudo mkdir /media/Data
```The line in fstab looks like this:
```
UUID=f7927995-b098-42be-ada0-987857f5177a /media/Data ext3 defaults,noatime 0 0
```Then do the mount -a thing again:
```
sudo mount -a
```Two different partitions with mount points in two different locations - one visible on the desktop - one not. Both are mounted automatically at boot.

---

