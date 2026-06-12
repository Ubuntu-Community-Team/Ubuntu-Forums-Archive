---
title: "nvraid problems"
date: 2009-02-11
forum: General Help
---

### Post by alex.galani on 2009-02-11
Hi guys..
I hope I'm in the right place to ask this question, and I certainly hope I haven't opened a thread that has already been discussed.
To cut a long story short, I'm new to linux. I have used Windows most of my life, although I have tried various distributions of linux over the years, I've never used any distro more than several weeks.

I've installed ubuntu 8.10 with WUBI on a hard drive different from that on which I've got windows. I have a RAID0 setup with nvraid onboard controller from my motherboard (650i). Although I can see my NTFS partitions, i can't see the raid one from ubuntu. I have tried using dmraid and it said nvraid was active...

I have no clue as to what to do so I can browse my files freely... Any suggestions?

---

### Post by fjgaude on 2009-02-11
You need to mount the raid0 first before you can browse it.

Study the man pages for dmraid. Make a mountpoint for the raid:

```
sudo mkdir /home/raid
```

You can use other than /home/raid as you wish.

Then find out what the raid is named using dmraid:

```
sudo dmraid -l
```

From there you will get something like a mapper name and then you can mount:

```
sudo mount -t ntfs /dev/mapper/nvidia_ahahbhbjaddg /home/raid
```

Let us know how you are doing.

---

### Post by aikiwolfie on 2009-02-11
[http://ubuntuforums.org/showthread.php?t=629459]("http://ubuntuforums.org/showthread.php?t=629459")

Give that a try. It might be a little out of date. I didn't think anybody had been reading it. Let me know how it goes.

---

