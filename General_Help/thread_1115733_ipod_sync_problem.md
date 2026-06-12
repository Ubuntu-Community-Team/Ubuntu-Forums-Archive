---
title: "ipod sync problem"
date: 2009-04-04
forum: General Help
---

### Post by wietsewietse on 2009-04-04
Hi there,

I'm a little new to this forum, but have been running Kubuntu (currently using 7.10 Gutsy Gibbon).

A friend gave me an Ipod Nano (8gb model no A1285), I believe this is a newer (second?) generation Ipod. Now I have been reading the previous threads on the problems other people have had with syncing these, to use the program Amarok for putting music on and stuff.

I tried both fixes in this thread: [http://ubuntuforums.org/showthread.php?p=5768591](http://ubuntuforums.org/showthread.php?p=5768591) but the first fix gives a link to download files, which gives a 404 and with the second fix I run into problems, mainly that the output from the konsole is different (when I enter the code). So I'm a little stuck now. 

First I thought it might be to do with settings in Amarok, as it does seem like the Ipod mounts (I can access the folders and files through Dolphin File Manager) but it continues to give this error:

" Media Device: failed to create lockfile on iPod mounted at /media/Wietse's iPod: Read-only file system "

Can someone help?

Thanks, Wietse

---

### Post by jamin_melville on 2009-04-04
Hey I used gtkpod to get my ipod working in linux. After setting up my ipod with gtkpod I have been able to sync with heaps of different programs.

---

### Post by wietsewietse on 2009-04-04
Thanks jamin_melville, I'll give this a try. However, just noticed that the fix I worked on before has now installed things which interfere with mounting the Ipod, something which did work before. 

[mntent]: warning: no final newline at the end of /etc/fstab
mount: mount point /media/ipod does not exist

I am unable to edit /etc/fstab or remove it and not sure how to do this (using konsole orso). Also, I don't really want to mess with stuff, in case I damage things..

Any advice?

---

