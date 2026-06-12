---
title: "Unable to mount floppy..."
date: 2005-06-05
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-06-05
I get the below error whenever I right-click on the disk-mounter that I have on my desktop...

---

### Post by kamstrup on 2005-06-06
What does your /etc/fstab say? What happens if you do "sudo mount -t vfat /dev/fd0 /media/floppy0"? and maybe "ls /media/floppy0"...

PS: All with the disk in, ofcourse :-)

Cheers

---

### Post by YourSurrogateGod on 2005-06-06
[QUOTE=kamstrup]What does your /etc/fstab say? What happens if you do "sudo mount -t vfat /dev/fd0 /media/floppy0"? and maybe "ls /media/floppy0"...

PS: All with the disk in, ofcourse :-)

Cheers[/QUOTE]
When I try mount...
```
mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
When I try ls, prints out nothing.

---

### Post by Takis on 2005-06-06
Can I ask a (potentially silly) question?

Have you actually formatted the disk?

---

### Post by YourSurrogateGod on 2005-06-06
[QUOTE=Takis]Can I ask a (potentially silly) question?

Have you actually formatted the disk?[/QUOTE]
I don't remember. What effect would it have if I did/didn't?

---

### Post by Takis on 2005-06-07
[QUOTE=YourSurrogateGod]What effect would it have if I did/didn't?[/QUOTE]
See your first post.  ;-) 


Try putting the floppy in and running```
$ mkfs.vfat /dev/fd0
```(Presumably there's nothing important on the floppy!)

---

### Post by YourSurrogateGod on 2005-06-07
[QUOTE=Takis]See your first post.  ;-) 


Try putting the floppy in and running```
$ mkfs.vfat /dev/fd0
```(Presumably there's nothing important on the floppy!)[/QUOTE]
I did, the below is what I got...
```
$ $ mkfs.vfat /dev/fd0
bash: $: command not found
```

---

### Post by sbassett on 2005-06-07
It looks like that pesky $ snuck in there some how. try :

mkfs.vfat /dev/fd0

---

### Post by LanM on 2005-06-07
Does the above require mtools?

---

### Post by YourSurrogateGod on 2005-06-07
[QUOTE=sbassett]It looks like that pesky $ snuck in there some how. try :

mkfs.vfat /dev/fd0[/QUOTE]
>_< Do'h!

I tried that and got...
```
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: failed whilst writing reserved sector
```

---

### Post by Takis on 2005-06-08
Oh, sorry, I use the $ to designate a terminal command (and differentiate commands from terminal output).

Try a different floppy disk for now. If that works, congradulations you've made yourself a drink coaster out of the first floppy (i.e. it's a dud). If it doesn't work, you may have a busted drive.

---

### Post by YourSurrogateGod on 2005-06-30
[QUOTE=Takis]Oh, sorry, I use the $ to designate a terminal command (and differentiate commands from terminal output).

Try a different floppy disk for now. If that works, congradulations you've made yourself a drink coaster out of the first floppy (i.e. it's a dud). If it doesn't work, you may have a busted drive.[/QUOTE]
Sweet, now I have a drink coaster where I can put my beer :) .

/mmm... Sam Adams :drool: .

---

