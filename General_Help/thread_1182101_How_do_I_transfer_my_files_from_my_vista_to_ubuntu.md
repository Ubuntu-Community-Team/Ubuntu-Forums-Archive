---
title: "How do I transfer my files from my vista to ubuntu jaunty(dual booted)?"
date: 2009-06-08
forum: General Help
---

### Post by Zeast3 on 2009-06-08
I have Ubuntu Jaunty dual booted Windows Vista home premium(vista installed first). 

I've been trying Ubuntu, and so far I like it alot more than windows. What I would like to know is how to transfer all of my files from Windows Vista to Ubuntu Jaunty, before I delete Windows Vista.

By the way, I'm running the dual boot on a gateway laptop which is why I need to get rid of one(cutting down alot of free space).

I asked this same question on yahoo answers and got this response

"Open a terminal.  Become root. 
mkdir /mnt/windows -- it's ok if it's already there.
ntfs-3g /dev/hda1 /mnt/windows if that doesn't work change hda1 to sda1.
exit root.
Browse with the ubuntu file manager to /mnt/windows
Then Documents & Settings/(your windows user name)
copy the files from desktop, My Documents, and wherever else to /home/(your linux user name).

To make sure you don't accidentally write to your windows drive type
umount /mnt/windows."

I followed the directions untill "Then Documents & Settings/Zane(my name)"  I tried typing documents & settings/zane together, then I thought he meant documents then search settings in documents, but that didn't work because I found 2 documents folders, and they were both empty.

I'm very new to this kind of thing, and would like to start reading more into what I can do with ubuntu, but I need my files first. please explain in detail.

---

### Post by philcamlin on 2009-06-08
put all your files on a pendrive and transfer it over like that 

its alot easier because windows cant read ext3 filesystem :)

---

### Post by michy99 on 2009-06-08
It will probably be easier for you to use nautilus (the graphical file browser) instead of the terminal to copy your files over. If you use the terminal you have to be sure to use the correct case in the path names. In linux, Documents is not the same as documents because one has a capital D and the other has a small d.

---

### Post by Einsamkeit on 2009-06-08
Hmm well unless I'm mistaken, you can directly mount your Windows partitions and take from them under Ubuntu. Windows can't read ext3, but Ubuntu can read NTFS.

At least that's how I do it with XP.

---

### Post by yaroto98 on 2009-06-08
Follow the instructions [here]("http://www.linux-faqs.com/Forum/viewtopic.php?t=7") in you ubuntu side to mount your partion. Then just copy over to your linux side whatever you want

*Note you may have to change ```
mount /dev/hda1 /mnt/windows -t ntfs -r
```

with

```
mount /dev/hda1 /mnt/windows -t ntfs-3g -r
```

---

### Post by Zeast3 on 2009-06-08
Actually, I used nautilus, and I thought that linux was case sensitive so I tried everything exactly as he said it on yahoo answers, and phil thanks, I'm going to try that soon.

---

### Post by Zeast3 on 2009-06-08
I have it mounted, what do I do to move the files?

---

### Post by Ubunt2u on 2009-06-08
as i do this quite often, i mount the windows partition in nautilus, navigate to the files i want, then simply copy or cut and paste to desired location on my ubuntu partion.
i've never had any issues doing it this way.

---

### Post by Zeast3 on 2009-06-08
Do you mind giving me an explanation on how to do that Ubunt2u? I've been trying since 10:00am(est), and I can't get any work done untill I transfer my files.

---

### Post by LucasCordina on 2009-06-08
simplest thing to do would be a pendrive.
or any optical device you can record your data onto ;)

---

### Post by Ubunt2u on 2009-06-08
> **Zeast3 said:**
> Do you mind giving me an explanation on how to do that Ubunt2u? I've been trying since 10:00am(est), and I can't get any work done untill I transfer my files.

In the "Places" tab, my windows partition shows up as 130gb drive i double click on it and it opens files in nautilus.  since the os is vista, i navigate to users, my name, the files/folders i want and then cut/copy the files/folders.  then in nautilus i click on home folder then navigate to where i want to place the files, then paste them.  
I can do screenshots if you want, but it will be later on before i can.  (im still at work right now.)

---

