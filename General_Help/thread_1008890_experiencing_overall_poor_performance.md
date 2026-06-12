---
title: "experiencing overall poor performance"
date: 2008-12-12
forum: General Help
---

### Post by perfect_circle on 2008-12-12
firefox crashes way more often than it should, or the screen grays out and stops, then it will come back... 

i also cannot get volume from vlc and firefox at the same time, either one works or the other.  also seems to just be running slower then when i was running 8.01.

i also noticed that when i boot(i have a dual boot with xp) it shows several more options than just ubuntu and xp, there are about 4 versions of ubuntu and all of the recoverys for each version.

oh and i also have humongous text for the log in screen.

any ideas what could be the problem, or anything i can check for that would clear things up. thanks in advance!

---

### Post by Sjeti on 2008-12-12
The text at login you can get rid of, however I strongly recommend you leave at least a back up kernel and a recovery of it.

You can get ride of all those other entries by opening up your menu.lst and commenting out (#) the entries you don't want.
```

sudo gedit /boot/grub/menu.lst

```

As far as the firefox issue, you really haven't given enough information...it could be a problem with firefox itself, or it might be a video driver issue or something, I honestly don't know.

---

### Post by 2hot6ft2 on 2008-12-12
> **perfect_circle said:**
> firefox crashes way more often than it should, or the screen grays out and stops, then it will come back... 

i also cannot get volume from vlc and firefox at the same time, either one works or the other.  also seems to just be running slower then when i was running 8.01.

Solution is here except the occasional greying out [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)


> i also noticed that when i boot(i have a dual boot with xp) it shows several more options than just ubuntu and xp, there are about 4 versions of ubuntu and all of the recoverys for each version.

System>Administration>StartUp Manager or if you don't have it search for "sum" in System>Administration>Synaptic Package Manager and install it.

When you open it click on the Advanced tab and you can choose whether or not to show the memtest and recovery options as well as how many kernels to show.

You should keep 2 kernels showing so if something stops working after a kernel update you can go back to the old kernel and a recovery option is a good idea as well.

The other way is to edit the menu.lst file and comment them out by hand using the # sign before them which gives you more flexibility in how it will appear. Your choice.

```
sudo gedit /boot/grub/menu.lst 
```

---

