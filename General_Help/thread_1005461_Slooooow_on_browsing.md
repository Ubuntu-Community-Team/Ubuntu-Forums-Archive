---
title: "Slooooow on browsing"
date: 2008-12-08
forum: General Help
---

### Post by naoli on 2008-12-08
Hi ubuntu gurus !

I have a weird problem. Every time a soft needs to browse the disk (firefox when I attach some files to a mail, evince when I try to save some pdf file, ...), it makes 10 secondes while the soft is frozen before it eventually accepts to process it and display the directory.

It happens whenever the directory it's trying to display and whatever the soft. When running nautilus, I have no problem so far.

My memtest turned OK and my disks seems allright :
```

$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1736 MB in  2.00 seconds = 868.57 MB/sec
 Timing buffered disk reads:  188 MB in  3.00 seconds =  62.61 MB/sec
```

I read this could be due to double entry in /etc/hosts so I removed one line :
```

~$ cat /etc/hosts
127.0.0.1 localhost naolidesktop
#127.0.1.1 naolidesktop
```

Of course, no change...I've got no idea  :confused:

---

### Post by naoli on 2008-12-10
I have a clue : programs using a kde interface seems not to be affected. Gnome should be guilty...

---

### Post by naoli on 2008-12-15
Hey, I think Gimp is guilty ! After rebooting, everything seems allright until I run Gimp... Even if I quit gimp, browsing gnome remains slow until I reboot again...

Any idea how to get rid of it ?

---

### Post by naoli on 2008-12-17
All right ! I got it ! That's not gimp, that's **trackerd** !

Trackerd is responsible for this, sorry for blaming gimp. A little 

> killall trackerd 

solved aaaaaall my problems. :)

---

