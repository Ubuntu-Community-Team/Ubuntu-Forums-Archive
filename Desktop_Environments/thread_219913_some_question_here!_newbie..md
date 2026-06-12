---
title: "some question here! newbie."
date: 2006-07-20
forum: Desktop Environments
---

### Post by CVDpr on 2006-07-20
Hey there:

1) How can i hide the file extension of files( .jpg, .mp3)
i dont want to see the Pic.png, Music.mp3 only Pic, Music without the extension.

2)I log in wih the root account to access my Windows partition
cuz with the normal user account(CVD) it always say "you dont have permission to do this  to do that",then copy the folder 
Music and paste it in the normal CVD Home, 

then switch back to the CVD account but i cant modified the files cuz the owner its the root, then switch back to root and change the folder Music permission to Owner= CVD, Group = CVD.

and now the folder Music permission say Owner = CVD , but all the fu**ing files inside the folder say Owner = root. 

I have to change the owner of every file inside the folder? 
how can i change the folder Music and all the files inside
Owner = root , to  Owner = CVD at once?

Thx. this security thing its start to annoying me. maybe i better
witch to the root account for ever...

3) Tell me whats the difference between root-volume and the 
Filesystem cuz both have the same folders and files inside. Check the picture please..

---

### Post by Ramses de Norre on 2006-07-20
1) Can't be done and this is a good thing, in windows they do things as music.mp3.exe to make people install malware.

2) You'll need to edit /etc/fstab to get access with your normal user, do ```
sudo gedit /etc/fstab
``` and post the contents here, we'll tell you what to change.

3) ```
sudo chown -R CVD:CVD /home/CVD/music
```

4) Root volume and file system are the same, I've never understood why there are two icons..

---

### Post by CVDpr on 2006-07-20
> **Ramses de Norre said:**
> 4) Root volume and file system are the same, I've never understood why there are two icons..

So , can i delete one ? Wich one?

---

### Post by CVDpr on 2006-07-20
I notice alot of automatically start-up processes, wich one are necesary to run ubuntu with-out problems and the ones that are unnecesary like "evolution.exe", how can i disable the unnecesary ones to start-up automatically?

---

### Post by muep on 2006-07-20
You can't delete it, as those are just shortcuts Gnome provides for you. It may be possible to switch one of them off, but don't try to remove anything as root from there -it might destroy everything on your computer.

There just are two shortcuts for the same thing. The Filesystem is for the filesystem the your operating system is running off. The other one is just because there appears to be shortcut for all available partitions.

---

### Post by muep on 2006-07-20
As default, Ubuntu starts mostly processes necessary to run Gnome and the underlying system. There are a few system services that can be disabled, but on most systems this will not affect performance much.

If it's the user processes that you are worried about, you shuold consider using some other system instead of Gnome. However, the Gnome processes are there for a purpose and using an other environment like Openbox of Icewm might be a bit difficult. It would require a lot of command line use, anyway.

Is your system behaving particularly slow?

---

### Post by CVDpr on 2006-07-20
....

---

### Post by CVDpr on 2006-07-20
> **muep said:**
> Is your system behaving particularly slow?

Nop, its fast, but i see more processes that my Winxp. and it consume more memory.

-----------------
AMD64-1.8ghz
512mb 400mhz
50gb=WinXp
90gb=Ubuntu

---

### Post by max_dingemans on 2006-07-20
Perhaps [This]("http://ubuntuforums.org/showthread.php?t=89491") thread would be help you turn off extra services.

---

