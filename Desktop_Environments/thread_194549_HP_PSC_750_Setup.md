---
title: "HP PSC 750 Setup"
date: 2006-06-11
forum: Desktop Environments
---

### Post by earlycj5 on 2006-06-11
I've tried following this thread: [http://www.ubuntuforums.org/showthread.php?t=121896&highlight=%22hp+scanner%22](http://www.ubuntuforums.org/showthread.php?t=121896&highlight=%22hp+scanner%22)

to no avail.  I can't get past the first step, I still get
```
 HP Linux Imaging and Printing System (ver. 0.9.7)
 Device URI Creation Utility ver. 2.5

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 Creating URIs for '/dev/usblp0':
 Trying bus: usb...
 Trying bus: par...
 [ERROR]: /dev/usblp0: Failed. Please check device node of device and try again.

```

I tried using the old hpoj driver.  That worked for the scanner but then cups wanted to install something other than the hpijs driver for my printer.

It doesn't even seem to recognize that the USB scanner is hooked up if I use the hplip driver but the hpoj does.  So I can set the printer up through cups as a USB printer but not if I have the hpoj configured.  When I try to set it up through cups it doesn't recognize that there's a "HP:" device attached so that won't work when I open the hp-toolbox to configure the scanner it says there's no printer configured through CUPS since I have to configure it as a USB printer.

So why won't this work with the hplip driver as the thread that linked too indicated it should?

I hope that makes sense.

---

### Post by tom56 on 2006-07-04
Same problem here with the same printer. Printing works, scanning doesn't.

---

### Post by gsmith on 2006-07-20
What worked for me was to install hpijs then run

```

sudo ptal-init setup

```

then follow the instructions that come up.  Hope this works for you.

---

### Post by 11hjpphty76lkjj on 2006-07-21
You also may want to consider using the latest HP linux driver.

[http://hplip.sourceforge.net](http://hplip.sourceforge.net)

---

### Post by ajesh on 2006-07-22
I tried the steps in the thread ([http://www.ubuntuforums.org/showthread.php?t=121896&highlight=%22hp+scanner%22](http://www.ubuntuforums.org/showthread.php?t=121896&highlight=%22hp+scanner%22)) and it worked for me fine. 
I can print and scan now. 
The only problem I had was with CUPS username and password, but I followed instructions in this thread: [http://ubuntuforums.org/showthread.php?t=193260](http://ubuntuforums.org/showthread.php?t=193260) and got it working.
Hope you got yours working....:)

---

### Post by keheikev on 2006-08-17
I put in the code that gsmith suggested but I do not get a gui to work with the scanner and nothing comes up. I went and saw the latest driver but I am a little unsure how to install it. So  I installed hpij hplip 0.9.7 although I am able to print no scanning is happening.
Kiheikev:confused:

---

### Post by Marshall2day on 2006-08-23
I had to do chmod 777 /dev/usblp0 first before I could use hp-makeuri command. After that it worked like a charm.

---

### Post by Unaha-Closp on 2007-01-12
Forever the newbie it seems, I've not managed to get the 'hplip' driver and related toolbox stuff to work with 6.06. However, I got printing and scanning to work by installing the 'hpoj' driver and using 'ptal-init setup'. This is probably a bit late for this thread, but what the hell, some late comer like me may find it useful.

---

### Post by Unaha-Closp on 2007-01-12
After reading the forums more closely, I've found out where the problem lies, and now have the newer HPLIP stuff working.  I tried "sudo chmod 777 /dev/usblp0" and it worked, however, only on a temp. basis. Every time  I restarted it's permissions were reset. Looking at the threads on dynamic node/device allocation etc, the problem ended up being in the "/etc/udev/rules.d/45-libsane.rules" file. Find your printer (HP PSC 750) and change the "MODE=0664" part to "MODE=0666". Now everything works fine every time! I can see how much ink I've got left:)

Thank you forum people.

---

