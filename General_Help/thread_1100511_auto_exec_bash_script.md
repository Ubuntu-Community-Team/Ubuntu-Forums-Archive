---
title: "auto exec bash script"
date: 2009-03-19
forum: General Help
---

### Post by nicola76b on 2009-03-19
Hi all.
I'd like to exec a bash script (that it'll check for a file presence, and, if exists, use it) every time an usb key is insert into pc. How can I do?

Where should I put this script and how can I auto exec it every time a key will be inserted?

Thank you very much,
    -nicola

---

### Post by albandy on 2009-03-19
you can monitorize /var/log/messages to see if a new entry of usb device appears
then accesing to it's mount point and finally executing the script

---

### Post by nicola76b on 2009-03-19
Hi, when I insert usb key /var/log/messages display

```
Mar 19 15:52:47 mio-laptop kernel: [47581.492727] usb 7-2: configuration #1 chosen from 1 choice
Mar 19 15:52:47 mio-laptop kernel: [47581.495533] scsi8 : SCSI emulation for USB Mass Storage devices
Mar 19 15:52:52 mio-laptop kernel: [47586.502512] scsi 8:0:0:0: Direct-Access     AF       USB_DISK         1.00 PQ: 0 ANSI: 2
Mar 19 15:52:52 mio-laptop kernel: [47586.504563] sd 8:0:0:0: [sdb] 1999872 512-byte hardware sectors (1024 MB)
Mar 19 15:52:52 mio-laptop kernel: [47586.507569] sd 8:0:0:0: [sdb] Write Protect is off
Mar 19 15:52:52 mio-laptop kernel: [47586.510436] sd 8:0:0:0: [sdb] 1999872 512-byte hardware sectors (1024 MB)
Mar 19 15:52:52 mio-laptop kernel: [47586.511589] sd 8:0:0:0: [sdb] Write Protect is off
Mar 19 15:52:52 mio-laptop kernel: [47586.516763]  sdb: sdb1
Mar 19 15:52:52 mio-laptop kernel: [47586.628294] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Mar 19 15:52:52 mio-laptop kernel: [47586.628963] sd 8:0:0:0: Attached scsi generic sg2 type 0
```

my device is recognized and automount under "/media/USB DISK". What I want is, EVERY time I insert a usb key, system will AUTOMATICALLY lunch "/home/mio-laptop/pippo.sh" 

Thank you,
   -nicola

---

### Post by albandy on 2009-03-19
ok you need to learn bash script programming
a simple loop wich reads the file every 1 or 2 seconds will work
save the date and hour in a variable
compare the variable to know if it's a new device
then load your script.

---

### Post by finer recliner on 2009-03-19
you might be able to write udev rule to do this...

---

### Post by nicola76b on 2009-03-19
I'm not a big programmer but I think this is not a good solution. The script you'll propose waste a lot of cpu time (I insert the key only one time every 2 or 3 days...)

I don't know very well linux, but I think that exist a demon that constantly motorized the insertion of new usb.
Moreover, I think there is a configuration file where, in somehow, I can tell the system "when new usb disk is insert lunch a script".

Your solution probably works, but I wont use cpu time for a dummy process..

However thanks a lot,
Best regards,
   -nicola

---

### Post by nicola76b on 2009-03-19
> **finer recliner said:**
> you might be able to write udev rule to do this...

I think this solution is better..
any tip?

or link to EASY guide (plese don't answer "use google", :) , I'm searching for a guide for DUMMY boy..)

Thanks,
    -nicola

---

### Post by albandy on 2009-03-19
> **nicola76b said:**
> I'm not a big programmer but I think this is not a good solution. The script you'll propose waste a lot of cpu time (I insert the key only one time every 2 or 3 days...)

I don't know very well linux, but I think that exist a demon that constantly motorized the insertion of new usb.
Moreover, I think there is a configuration file where, in somehow, I can tell the system "when new usb disk is insert lunch a script".

Your solution probably works, but I wont use cpu time for a dummy process..

However thanks a lot,
Best regards,
   -nicola


the execution time of an script of this kind is 0m0.005s and you set it to sleep 0m2.000s 
so a cost of 0.005s every 2.000s it's near to 0.

---

### Post by finer recliner on 2009-03-19
if you were really going to write a bash script to check something every X number of seconds, days, weeks, whatever, you would add a cron job that calls a bash script. imo, its still a waste, no matter how quickly it may finish.

---

### Post by finer recliner on 2009-03-19
[http://reactivated.net/writing_udev_rules.html#external-run](http://reactivated.net/writing_udev_rules.html#external-run)


this may be what you need, i kinda just skimmed it though.

---

### Post by albandy on 2009-03-19
crontab don't let you specify seconds, only minutes and bigger time measurements.

---

### Post by nicola76b on 2009-03-23
> **finer recliner said:**
> [http://reactivated.net/writing_udev_rules.html#external-run](http://reactivated.net/writing_udev_rules.html#external-run)


this may be what you need, i kinda just skimmed it though.


This seems perfect solution WITHOUT any time-wasting. Here I found the solution, now the system automatically run the script when MY DRIVE is added in the system. (I create new rule)

```
KERNEL=="sdb", ACTION=="add", ATTRS{vendor}=="AF      ", ATTRS{model}=="USB_DISK        ", RUN+="/usr/bin/copyGuide.sh"

```


BUT I have already a problem. If the script copy or create files in HD or elsewhere works, but if I need to crete them INTO the key just inserted doesn't work. I think the problem is that the device already inserted is not already mount.

Any tips?

  -nicola

---

### Post by finer recliner on 2009-03-23
If I'm understanding correctly: you're trying to copy files onto the flash drive when its inserted (automatically), but its not mounted yet when its inserted (and the udev rule is called).

I would trying putting a sleep() call at the beginning of your shell script. maybe 2 or 3 seconds...just enough time to let linux mount the drive before the rest of the script runs.

---

### Post by nicola76b on 2009-03-23
I just try that..
I add "sleep 20" (20 seconds) in my script, and the system seems wait 20 seconds BEFORE mount the device (I don't konw why, I also try to rename my rule as "98-copyGuideXMLonUSB.rules", so it should become the LAST rule executed)

Who care about mount new device in linux system?
I start thinking that this rule are ALL executed BEFORE mount procedure..

However thanks for quickly answer!!

  -nicola

---

