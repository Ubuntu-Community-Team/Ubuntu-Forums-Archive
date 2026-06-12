---
title: "Hotsync Palm via Bluetooth"
date: 2006-06-08
forum: Desktop Environments
---

### Post by fluid_motion on 2006-06-08
I have been using hotsync to connect my Palm via bluetooth in Windows to update Palm Desktop. Its connected via a Bluetooth serial connection using the Bluetooth software. I want to do likewise with Jpilot in Ubuntu. Has anyone managed to do this?

I have looked through quite a number of tutorials and tips but all of them provide procedures to connect it to internet. I would not mind if it connected as LAN using Bluetooth as long as I can hotsync my Palm wirelessly. Any help on this would be appreciated. Thanks!

---

### Post by thearif on 2006-06-11
Same here. 
I've been trying to find a way to sync my palm tungsten e2 with my laptop over bluetooth too but could not find anything neither. If anyone knows how to do this, please enlighten us :)

---

### Post by saaz on 2006-06-26
Me three. This would be a nice alternative to the udev hell which is preventing me (and everyone else it sounds like) from syncing with Dapper.

---

### Post by pito on 2006-06-27
Me no. fourth....

I have been 100% linux user for the last two years, but the latest Draper update just killed me ( in Norwegien Drap = Kill, so Draper means killer). I am not able any more to synch my palm.

Looks like there are more people on bad trail....

I have heard some people stating that they have occassionally be able to synch. I managed it three times in 50 tries.

There has been rumors that kernel 2.6.15 is the cause to the problems, seen some people having problems on the Suse 10.1 after latest update.

There has been notified that the new 2.6.17 works fine.

I will wait and see. Meanwhile I will try to change in the GRUB to boot with the old kernel I used in U-5.10. I will let you know in case of some positive results.

/piotr

---

### Post by pito on 2006-06-28
I had BIG problems to synchronize TE2 after I updated to Draper.

I managed it to synch with pilot-xfer only three times out of maybe hundreds. 
I tried different tricks, nothing helped.

But...after rumors that kernel 2.6.15 is broken regardin udev and usb stuff.

What I did today was that I switched back the kernel from Version 2.6.15 to 2.6.12, and the sync works every time both from command line,pilot-xfer, and via jpilot.

I recovered the old archived manu.lst~ from Breeze and rebooted the OS.
Then I ran "sudo modprobe visor" and I am back in the bussines.

There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

Hope it will help others.

/piotr

---

### Post by jkrolen5500 on 2006-06-29
>>There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

>>Hope it will help others.


How do I manage to get this new kernel, and did you mean Dapper??

---

### Post by jkrolen5500 on 2006-06-29
I have sucessfully synced palm with bluetooth!! I used these instructions 
[http://www.toobusyto.org.uk/tech/tungsten_linux.html](http://www.toobusyto.org.uk/tech/tungsten_linux.html) to help..

Main part is to follow these here .. Hope this  helps someone



   1.   Load the hotsync application, and go to the "Modem Sync Prefs" menu and select "Network".
   2. On the LanSync prefs menu, choose "Local HotSync".
   3. Now go to the "Primary PC Setup" menu and enter the details of the PC you want to HotSync with. To to save time on a DNS lookup, I entered the IP address rather than the hostname (Where it says PC name put the IP address.  I didn't have to put the ip address in reverse like this says) . Unfortunately, there is a bug in OS 5.0 that causes the palm to get the IP address wrong, if your machine's IP address is 172.31.64.12 it will try to send to 12.64.31.172 instead. I believe this might be fixed in the latest OS patch for the Tungsten, but if not, you can get around it by simply entering the IP address "backwards" (i.e. enter 12.64.31.172 to get it to sync with 172.31.64.12). The Subnet Mask is optional - it defaults to 255.255.255.0.
   4. Finally, on the main HotSync screen, select "Modem" and then choose the network connection to your PC. To perform the hotsync, setup the PC as detailed below and then tap the button in the centre of the screen.

---

