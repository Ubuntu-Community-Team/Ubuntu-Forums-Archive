---
title: "printer v313 not working with 11.10"
date: 2011-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by orengolan on 2011-10-23
I have Dell Printer V313 (All-in-One).
It used to work with ubuntu 11.4 but after upgrading to 11.10 it stopped working.
I download the driver - dell-inkjet-09-driver-1.0-1.i386 and during the setup there is a screen
that ask me to connect the usb cable from the printer to my laptop. even though I connect it the next button is still disabled.

Any ideas except downgrading my ubuntu to 11.4?

---

### Post by cnobile on 2011-10-29
It seems that no printers are working on 11.10. They can be configured but won't print anything.
See: [http://ubuntuforums.org/showthread.php?t=1862862](http://ubuntuforums.org/showthread.php?t=1862862)

---

### Post by smallblackanimal on 2011-10-30
I have the same printer running on 32bit.

This worked for me....

```
 lsmod | grep usblp 
```

If it outputs nothing then...

```
 sudo modprobe usblp 
```

re-run

```
 lsmod | grep usblp 
```

you should get an output similar to this

```
jon@jon-desktop:~$ lsmod | grep usblp
usblp                  17833  0 
jon@jon-desktop:~$ 

```

Then restart cups

```
sudo service cups restart
```

Try your printer, it should work now. I spent at least a week trying to figure this one out. I'm also running kernel 3.0.0-13 from the proposed sources, not sure if that matters but you never know.

edit: You'll have to do this every time you reboot. You can add *usblp* to the /etc/modules to have it load at start up every time.

---

### Post by orengolan on 2011-10-31
thanks to both of you for your help!
I already installed 11.04 but as soon as i'll be brave to get 11.10, i'll try both of your suggestions.

I hope that by the time i'll upgrade, it will work out-of-the-box.

---

### Post by bigpapapump on 2012-01-22
That worked for me!  I was spinning my tires on this one.  Thanks for the help (this got me past the screen waiting to find the printer via usb too).

---

