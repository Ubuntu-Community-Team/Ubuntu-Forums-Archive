---
title: "[SOLVED] sshfs mp3fs server flac mp3 ipod etc"
date: 2009-01-10
forum: General Help
---

### Post by nothingspecial on 2009-01-10
I have a media server.

I have a of of flacs

I don`t have the space for a mp3 mirror.

There`s a great sounding app called mp3fs which mounts a directory full of your flacs in mp3 format without them actually being there. When you open or move them it coverts them on the fly. How cool is that?
So you mount this directory to your client and anytime you want to transfer a flac to your mp3 player it converts it for you. Brilliant. [[COLOR="Red"]Have a look[/COLOR]]("http://mp3fs.sourceforge.net/#how-it-works")

Problem is I can`t get the damn thing to work.

I start it exactly how it says

> mp3fs /mnt/music,128 /mnt/mp3 -o allow_other,ro obviously using the correct paths and when I try to open it (testing on my laptop even shows a mounted file system on my desktop) I get cmdline "no such file or directory" nautilus "no application ....."

I`ve chowned and chmoded as much as I know and sudoed and all sorts but I cannot get the damn thing to work.

Anyone know what I`m doing wrong.

Btw I love rockbox but it doesn`t work on the thingy connected to my car stereo (main ipod usage)

---

### Post by albinootje on 2009-01-10
> **nothingspecial said:**
>  There`s a great sounding app called mp3fs which mounts a directory full of your flacs in mp3 format without them actually being there. When you open or move them it coverts them on the fly. How cool is that?

Awesome! Thanks for sharing :)
> 
I start it exactly how it says

Quote:
mp3fs /mnt/music,128 /mnt/mp3 -o allow_other,ro

I just tested it myself as following :
```

mkdir /tmp/test; mp3fs /home/albinootje/Music,128 /tmp/test -o allow_other,ro

```
And, using Nautilus, it works.

Did you not get any errors at all ?
Try :
```

dmesg

```

Did you mount it with sudo or not ?
Is your user in the fuse group ?
```

groups

```

---

### Post by nothingspecial on 2009-01-11
Must have been something to do with the bit rate I was using. I was trying 192.
Simply changing it to 128 makes it work. Don`t know why.

Thanks

---

