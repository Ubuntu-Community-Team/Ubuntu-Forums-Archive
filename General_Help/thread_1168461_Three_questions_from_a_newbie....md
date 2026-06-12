---
title: "Three questions from a newbie..."
date: 2009-05-24
forum: General Help
---

### Post by Aquaquad on 2009-05-24
Hallo

1. I updated from Ubuntu 8.10 to 9.04 but in grub there aren't any new entries for 9.10, only the ones with 8.10 and the old kernel (2.6.27-7). I used the command update-grub but nothing happened. 

My usr/src/:
```
root@root:/usr/src$ ls -l
&#963;&#973;&#957;&#959;&#955;&#959; 55760
drwxr-sr-x  9 root src      4096 2009-05-23 17:30 Alsa-1.0.20
lrwxrwxrwx  1 root src        30 2009-05-22 17:23 linux -> linux-headers-2.6.27-7-generic
drwxr-xr-x  2 root root     4096 2009-05-23 18:29 linux-headers-2.6.27-7-generic
drwxr-xr-x 22 root root     4096 2009-05-20 06:24 linux-headers-2.6.28-11
drwxr-xr-x  7 root root     4096 2009-05-20 06:24 linux-headers-2.6.28-11-generic
drwxr-xr-x 25 root root     4096 2009-01-15 21:09 linux-source-2.6.27
-rw-r--r--  1 root root 57008963 2009-04-17 06:41 linux-source-2.6.28.tar.bz2
drwxr-xr-x  3 root root     4096 2009-05-20 06:24 nvidia-180.44
```2. After the update the sound is not working properly. Sometimes I am able to hear, sometimes I hear only crackling sounds, others I cannot hear anything or I can hear with a particular player (Amarok) but I can't with VLC. My soundcard is an on-board HDA Nvidia. I tried to solve it but installing PulseAudio drivers but nothing happened. Now I have both ALSA and PulseAudio installed.

Output of the command "wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh":
[http://www.alsa-project.org/db/?f=ede7f312cd9d3cc1817b1f66fc7f495bfc81c108](http://www.alsa-project.org/db/?f=ede7f312cd9d3cc1817b1f66fc7f495bfc81c108)

3. I am hearing a high-pitced sound from the computer. With Windows I don't hear such a sound. It seems that it isn't the CPU. But the system uses steadily about 30% of the RAM even without doing nothing. Why it uses so much ram? 

Thanks in advance...

---

### Post by alphacrucis2 on 2009-05-24
Can you see what kernels are actually in /boot


```
ls /boot
```

The above will show the files there, Or you can just have a look from Nautilus to see if the later kernels are actually there.

---

