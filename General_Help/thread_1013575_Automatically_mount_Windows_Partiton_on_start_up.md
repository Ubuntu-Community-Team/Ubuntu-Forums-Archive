---
title: "Automatically mount Windows Partiton on start up?"
date: 2008-12-17
forum: General Help
---

### Post by SirSigma on 2008-12-17
For awhile, I've really grown tired of having to manually mount my C drive from Windows because I have all my music and videos on it (that way I can easily access the media from both Ubuntu and Vista whenever I need to).

Now I've done some searching on a way to automatically mount my C drive on start-up. I know that it's "/dev/sda2" (according to ntfs-config, which I'm not completely sure on how to use; I installed it trying to figure out how to automatically mount it in the first place) on mount point "/media/SQ004668V05" It's also an NTFS partition.

Are there any instructions on how to specifically mount this on start-up? I found some instructions for other scenarios, but I'm afraid that if I try them they may not work for me.

Also, I'm using Intrepid.

---

### Post by dcstar on 2008-12-17
> **SirSigma said:**
> For awhile, I've really grown tired of having to manually mount my C drive from Windows because I have all my music and videos on it (that way I can easily access the media from both Ubuntu and Vista whenever I need to).

Now I've done some searching on a way to automatically mount my C drive on start-up. I know that it's "/dev/sda2" (according to ntfs-config, which I'm not completely sure on how to use; I installed it trying to figure out how to automatically mount it in the first place) on mount point "/media/SQ004668V05" It's also an NTFS partition.

Are there any instructions on how to specifically mount this on start-up? I found some instructions for other scenarios, but I'm afraid that if I try them they may not work for me.
.....

Install the **pysdm** package and use it to set things up:

System-Administration-Storage Device Manager

---

### Post by SirSigma on 2008-12-17
Wow, it worked! Made everything much easier! Thank you!

---

### Post by Tim Sharitt on 2008-12-17
There is a nice how to for fstab [here]("https://help.ubuntu.com/community/Fstab") and another one [here]("http://ubuntuforums.org/showthread.php?t=283131") which has a lot more information on managing partitions.

---

### Post by dcstar on 2008-12-17
> **SirSigma said:**
> Wow, it worked! Made everything much easier! Thank you!

It's a nice tool that saves people from manually hacking their fstab file, I don't know why it is not installed by default to give the "normal" computer user an easier way of doing this sort of thing.

---

