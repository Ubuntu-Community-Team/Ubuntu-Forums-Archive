---
title: "help with accesing Ubuntu partition from Windows"
date: 2005-12-21
forum: General Help
---

### Post by ubuntu27 on 2005-12-21
&#12371;&#12435;&#12395;&#12385;&#12399; I need your help guys!
I need to acces my Ubuntu partition from Windows.
I've search for it... but I only found Virtual Desktopslike [NoMachine](http://www.nomachine.com/) and [VMware](http://www.vmware.com/)

I don't what I need to use. I only want to Acces my Windows partition so I could burn (backup) my files from Windows with Nero.

Maybe there is some tweak, trick or another app that I need to use?

---

### Post by ksudbury on 2005-12-21
I use explore2fs to access linux partitions in windows.

---

### Post by canadianwriterman on 2005-12-21
You can't access a Linux partition from Windows. Windows just won't recognize it. If you want to back-up Windows files, you should add the Windows partition to fstab in Ubuntu and then do your backup from Linux.

---

### Post by ksudbury on 2005-12-21
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

works with ext3 as well...

---

### Post by chaumurky on 2005-12-21
If you want to pay (not much), Paragon Mount Everything installs a low level driver to allow you to mount a linux partition with a drive letter in disk management. It's quite fast too.

---

### Post by BathroomNinja on 2005-12-21
If your Ubuntu partition is ext2 or ext3, [http://www.fs-driver.org/](http://www.fs-driver.org/) will also allow Windows to see it (that's what I have running) and it's also free.

Of course, if you are using rfs, then it won't help at all.



VV---- No problem.  I found it from another user who helped me out once.

---

### Post by Rackerz on 2005-12-21
[QUOTE=BathroomNinja]If your Ubuntu partition is ext2 or ext3, [http://www.fs-driver.org/](http://www.fs-driver.org/) will also allow Windows to see it (that's what I have running) and it's also free.

Of course, if you are using rfs, then it won't help at all.[/QUOTE]

Thanks for that, it's better than explore2fs for me. :)

---

### Post by ubuntu27 on 2005-12-21
Thank you for your replies guys/girls! :KS 

I have ext3... I'm going to try to use  [Ext2 Installable File System for Windows](http://www.fs-driver.org/) or [Explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

Did soem of you tried both? Which one do you recommend? [Which one is better?]


Thank you in advance :)

---

### Post by Rackerz on 2005-12-21
I recommend [http://www.fs-driver.org](http://www.fs-driver.org) I'm using it now. It's a excellent! Make sure you set a drive letter for your Linux partition so you can see it ;). It's brilliant!

---

### Post by ubuntu27 on 2005-12-21
Thank you Rackerz.
Hey, Can I create mount Linux partition as WRITE only with "Ext2 Installable File System for Windows" I've read that it can write into the Linux partition... and I think that is a security hole. 

I don't want Windows to have complete control over my Linux...

I just want a Read only. ;) 

Sorry if I am asking too much question.
But I am currently decesperate trying to do backup of both my files that are in Windows and files that are in Ubuntu.

[QUOTE=canadianwriterman]You can't access a Linux partition from Windows. Windows just won't recognize it. If you want to back-up Windows files, you should add the Windows partition to fstab in Ubuntu and then do your backup from Linux.[/QUOTE]

I mounted my Windows partition in Linux…
But, I cannot burn CD using K3b or nautilus because of lack of space in my Linux partition…   
See this thread: [http://ubuntuforums.org/showthread.php?t=106615](http://ubuntuforums.org/showthread.php?t=106615)

That is why I want use Windows to backup.

---

### Post by rcerreto on 2005-12-21
If you are concerned about security, why not using a samba share?
That would allow you to acces files from windows retaining full control on permissions.

---

### Post by BathroomNinja on 2005-12-21
Windows won't take control over the partition.  Just don't run around deleting things.  Copy and paste what you need and you will be fine.  Windows will try to make thumbnails out of picture directories, but you can stop that by changing your view in windows to 'list' instead of 'thumbnails' with the toolbar.


He can't use samba because it's on the same computer.

---

### Post by rcerreto on 2005-12-21
[QUOTE=BathroomNinja]He can't use samba because it's on the same computer.[/QUOTE]

I'm getting old :???:

---

### Post by BathroomNinja on 2005-12-21
[QUOTE=rcerreto]I'm getting old :???:[/QUOTE]

It happens to everyone ;)

---

