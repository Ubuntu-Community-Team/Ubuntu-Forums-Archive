---
title: "Lots of questions but this one's more important than most"
date: 2006-05-07
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-05-07
I have lots of questions, but here is the most important series.


1) I, through stupid user error, had to reinstall Ubuntu. I reinstalled it as Kubuntu BUT- here is where the error part comes in. A long time ago, before I dumped Windows XP altogether, I had a 20GB HDD w/ Linux on it. It had a ~900MB swap partition, ~2.5GB windows/linux file trade partition, and the rest was linux. Now, I am unable to resize the largest, almost empty ~16GB partition, resize the 2.5GB partition that Kubuntu accidently installed to in order to avoid losing files, and resize my 100GB NTFS partition to avoid losing files on there. I can back up the files, but I really want to avoid doing so and reinstalling again. This would be the fourth reinstall throughout Ubuntu's life on my PC. Help, please.

That leads to this. I have been trying to play my music library on the NTFS- I use captive-ntfs and always have to no problems. Before I installed Kubuntu instead of KDE'd Ubuntu, I could play MP3s. Now, I can't, so I tried to get Xine. I can't install the package because of dependencies, and I also can't install QParted (which I need, apparently) due to dependencies, because I don't have access to any online repositories through Adept- only the ones on the CD I made.


I can probably do the resize on the 20GB drive myself BUT- I can't get my Ubuntu Live! CD to NOT use the swap space, therefore locking the drive from editing like that. This last paragraph is probably the one that would solve (almost) all of my problems if answered.

---

### Post by gondilon on 2006-05-07
which order are your parititons on the drive?

---

### Post by az on 2006-05-07
[QUOTE=Your Name Is]

I can probably do the resize on the 20GB drive myself BUT- I can't get my Ubuntu Live! CD to NOT use the swap space, therefore locking the drive from editing like that. This last paragraph is probably the one that would solve (almost) all of my problems if answered.[/QUOTE]

sudo swapoff -a

Also, use ntfsresize to shrink your partition, if gparted will not.  Use it from the command line.

---

### Post by Wr8EYilK8Y on 2006-05-08
GParted will not, so where can I find this ntfsresize tool? I'm sorry- I'm not NEW to Ubuntu (I went from beginner to medium-advanced quickly) but I'm still new to some things in it- I discovered last week that Ubuntu, if KDE'd, likes to boot into command lines instead of GUI.

HDD1
|
|--~16GB
|
|--~2.5GB
|
|--~900MB

HDD2
|
|--full-sized NTFS


THanks for the swap tip- I'm assuming I run that in the Terminal?

---

