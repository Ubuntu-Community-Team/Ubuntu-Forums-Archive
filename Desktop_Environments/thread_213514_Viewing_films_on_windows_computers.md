---
title: "Viewing films on windows computers"
date: 2006-07-11
forum: Desktop Environments
---

### Post by tmafcerqueira on 2006-07-11
Hi. I'm using Kubuntu 6.06 and I wanted to view movies using samba and MPlayer. The problem is that when I try to do that I'm required to "download"(pass it from the windows computer to my own) the file. As I'm using Wireless this tends to be very slow. Is there any way of seeing movies on the network the way we see on windows?
Thanks,

---

### Post by Thund3rstruck on 2006-07-11
Yes, it's actually really easy. But you need to mount the network share to a folder. You cannot use the built-in gnome network browser interface to do it. 

make a folder:
```

mkdir -p /media/movies

```

mount the share
```

mount -t smbfs -o username=UserName,password=Password //servername/ShareName /media/movies

```

No view the movie in the mounted share /media/movies/MyVideo.mpg

---

### Post by jimbren on 2006-07-11
You might want to think about installing some sort of streaming server on the machine you're serving from.  

There's a very nice app called [Gnump3d]("www.gnump3d.org") that would do the job with very little overhead, and is probably less comlicated than the way you're currently doing it.  It runs in both 'nix and Windoze.  While it was originally designed for streaming mp3s, it handles most video formats without a problem.

---

### Post by tmafcerqueira on 2006-07-11
I'm going to try the first solution tonight. I'll let you know what happend. 
Thank you both.

---

### Post by tmafcerqueira on 2006-07-11
> **Thund3rstruck said:**
> Yes, it's actually really easy. But you need to mount the network share to a folder. You cannot use the built-in gnome network browser interface to do it. 

make a folder:
```

mkdir -p /media/movies

```

mount the share
```

mount -t smbfs -o username=UserName,password=Password //servername/ShareName /media/movies

```

No view the movie in the mounted share /media/movies/MyVideo.mpg

I've tried that, but I get an error message (I'll try to translate as best as possible):```

mount: type of archive file system incorrect, invalid opcion, invalid superblock em //10.0.0.1/e,
       code page missing or other error
       In some cases you can find important information on the system log. Try "dmesg | tail"
```

After trying dmesg I get the following:
```
[4295723.202000] smbfs: mount_data version 1919251317 is not supported
```
Do I need to install a package?
Thanks again for the help

---

### Post by GFBurke on 2006-07-12
It may not be excactly what you want, but you could use VLC on the Wind0ze PC and stream it with that..  that's what it's made to do.

---

### Post by tmafcerqueira on 2006-07-12
No, I can't because I'm using a very old computer, a pentium 3 with windows XP. You can image ao slow the movie would go:mrgreen:

---

### Post by carontis on 2006-07-12
Well, that can depends on how much ram you have, 'cause I've watched movies on PIII with 256 ram and only 16 vram... and using VLC. I think it runs... also if not perfectly.

---

### Post by tmafcerqueira on 2006-07-12
It has 128MB. Believe me, it's not an option.

---

