---
title: "Minimal - Shutdown problems"
date: 2012-03-07
forum: Desktop Environments
---

### Post by anXieTyPB on 2012-03-07
Hello there!
 
my HTPC with minimal Ubuntu Oneiric 32 bit and XBMC installed has one serious issue: shutdown does not work properly.
When I try shutting the machine down using XBMC, the shutdown is initiated but not completed (see below).
 
Entering 
```
sudo shutdown -h 0
```
in terminal also causes problems with my machine. I tried googling but i didnt really get any useful information.
All I see right now is the following:
```
Asking all remaining processes to terminate... [OK]
All processes ended within 1 seconds [OK]
Deconfiguring network interfaces [OK]
Deactivating Swap [OK]
Will now halt
[76.336770] Power down.
```
My screen is frozen now, no input can be made and i have to force a shutdown by pressing the power button for 5 seconds.
 
Taking a look at kern.log and boot.log was not successful either.
 
Mainboard: ASrock E350M1 with latest available BIOS installed.
 
Hopefully someone might be able to help me.

---

### Post by winh8r on 2012-03-07
You can also try

```
sudo poweroff now
```


If the system hangs, try this to avoid shutting down using the power button:

Press and hold down the ALT key

Press and release the PrintScreen key

type these letters

R E I S U B

This will cause the machine to safely shutdown and reboot and prevent potential filesystem damage from using the power button method.


It might also be worthwhile trying to allow the system longer to shutdown when using the 

sudo shutdown -h method

try using 

```
sudo shutdown -h 2
```

to allow more time for remaining processes to end properly

Hope this helps

---

### Post by anXieTyPB on 2012-03-07
```
sudo poweroff now
```

Does not work either. Worked twice and at the third time, same problem, now even with a blurry, strange screen (text display is totally distorted across the screen).


> If the system hangs, try this to avoid shutting down using the power button:

Press and hold down the ALT key

Press and release the PrintScreen key

type these letters

R E I S U B

This will cause the machine to safely shutdown and reboot and prevent potential filesystem damage from using the power button method.

No reaction. Tried this multiple times, no success.


When entering the console this time, i got welcomed with the following message:

```
sp5100 tco timer mmio address 0xbafe00 already in use
```


Delaying the shutdown with

```
sudo shutdown -h 2
```

didnt work either.

:(

---

### Post by winh8r on 2012-03-07
I did find this thread :

[http://ubuntuforums.org/showthread.php?t=1812698]("http://ubuntuforums.org/showthread.php?t=1812698")

The last post in that thread seems to have solved the issue for that user but those issues seem to be splash screen related rather than specifically to do with shutdown issues you are having.

Are you running a desktop environment on your minimal install or is it command line only?

---

### Post by anXieTyPB on 2012-03-07
Command line only! (Starting XBMC in XServer)

---

### Post by winh8r on 2012-03-08
Take a look at post #1 in this thread, about the script he uses to shutdown xbmc, might help you.

[http://forum.xbmc.org/showthread.php?t=32891]("http://forum.xbmc.org/showthread.php?t=32891")

Hope so.

---

### Post by anXieTyPB on 2012-03-08
Sadly I dont think this script is going to work for me.
It does what I was doing all the time...

When I'm rebooting by using ```
sudo reboot
``` the reboot is ALWAYS (tested 20 times) successful.


I just read my Motherboard's BIOS update log and they say 
> Fix Ubuntu 11.04 can not shut down issue. something that might be interesting has been applied in the last BIOS update.
Sadly enough, my BIOS version is up to date and I still have those shutdown problems...

---

### Post by winh8r on 2012-03-08
Try shutting down using the console (tty1)

control + Alt + F1

username and password

```
sudo shutdown -P now
```

might work, worth a try

---

### Post by anXieTyPB on 2012-03-10
Problem persists.

Tried installing 11.04 but i cannot shutdown there properly either.

I think it's a hardware defect, more detailed a motherboard defect....

---

### Post by anXieTyPB on 2012-03-11
Tested Windows 7 again.

Worked like a charm. 10 times in a row standard shutdown without any problems.

Is there a possibility to simulate a windows shutdown-signal for the BIOS in linux?

---

### Post by winh8r on 2012-03-11
Try having a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1938984]("http://ubuntuforums.org/showthread.php?t=1938984")

you might be able to reconfigure the /etc/rc0.d to get it to shutdown.

Hope this is of some help .

---

### Post by matthijskooijman on 2012-06-20
It seems this is really a BIOS bug, but the BIOS fix (1.50) did not work. I have two similar boards (E350M1 and E350M1/USB3), which have similar BIOS versions. On the E350M1/USB3, the 1.50 BIOS fixes this problem, but not on the E350M1. I've just contacted Asrock about this, hopefully they can fix this in the BIOS.

---

### Post by LiamOS on 2012-06-20
I usually use
# shutdown -Ph now
I remember having some problems with other commands, and this one seems to work perfectly on every distro I use.

---

### Post by nadro on 2012-07-21
I have the same problem in second PC (MB: ASrock E350M1), when I installed Ubuntu (currently 12.04). I checked ASrock site and they released 1.70 UEFI:
> [I]1. Improve keyboard / mouse compatibility.
2. Modify Ubuntu 12.04 can not shutdown issue.[/I]
I can't check it now (I will have an access to second PC in August), but I hope that this will solve Your and my problems with freeze a PC at shutdown. Please inform me if this fix Your problems :)

You can get v1.70 here: [http://www.asrock.com/mb/download.asp?Model=E350M1&o=BIOS](http://www.asrock.com/mb/download.asp?Model=E350M1&o=BIOS)

---

### Post by nadro on 2012-08-22
I have good news. I can confirm that BIOS v1.70 for AsRock E350M1 fixes problems with a shutdown on Ubuntu 12.04. Now a shutdown works like a charm :)

---

