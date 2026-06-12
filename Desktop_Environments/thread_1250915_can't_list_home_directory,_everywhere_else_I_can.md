---
title: "can't list home directory, everywhere else I can"
date: 2009-08-27
forum: Desktop Environments
---

### Post by denarced on 2009-08-27
the title pretty much says it all
I've tried this with gnome-terminal,xterm and nautilus
weird bug .. I'm sure it'll pass after reboot
Interesting thingie thou
Any ideas?

---

### Post by DaithiF on 2009-08-27
what command(s) are you running in the terminal.  what output do you get?

---

### Post by denarced on 2009-08-27
> **DaithiF said:**
> what command(s) are you running in the terminal.  what output do you get?

I ran ls and ls -l through an alias(ll)
no output, moves to next line and if you press ^c, it prints that and no action follows

---

### Post by DaithiF on 2009-08-27
in a new terminal, can you try these & post the output:
```
pwd
whoami
ls -ld /home/$(whoami)

```

thanks

---

### Post by wojox on 2009-08-27
What about 

```
ls -al
```

Show anything hidden?

---

### Post by denarced on 2009-08-27
DaithiF, your commands gave expected results
wojox, yours resulted in same buggy behaviour
look for included image to see for yourself

I was actually right, the problem was gone after reboot.
But I was able to re-create the problem.
I have a laptop and desktop, both ubuntu 9.04, all updates made
Laptop has nfs.
Here's what I did
1) mount the laptop
```
sudo mount 192.168.11.3:/home/denarced/ /home/denarced/lap/
```
2) shut down the laptop without umount
3) afterwards this problem occurs

weird

---

### Post by DaithiF on 2009-08-27
so i guess ls is hanging waiting for a reply from the (unavailable) laptop location.  can you ls a specific file in your desktop's home directory?  in any case, you can  just sudo umount /home/denarced/lap to unmount the laptop and you should be back to normal.

---

### Post by denarced on 2009-08-27
> **DaithiF said:**
> so i guess ls is hanging waiting for a reply from the (unavailable) laptop location.  can you ls a specific file in your desktop's home directory?  in any case, you can  just sudo umount /home/denarced/lap to unmount the laptop and you should be back to normal.

yep, that sounds logical and it fixed the problem
```
sudo umount lap
```
doesn't work btw
force-option is needed
```
sudo umount -f lap
```

---

