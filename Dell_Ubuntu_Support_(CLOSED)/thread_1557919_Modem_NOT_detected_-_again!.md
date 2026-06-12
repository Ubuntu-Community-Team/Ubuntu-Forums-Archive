---
title: "Modem NOT detected - again!"
date: 2010-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cracklins on 2010-08-21
Hello!

Back again.

For reference, please see my last comment on this thread before reading further:

[http://ubuntuforums.org/showthread.php?t=1523320](http://ubuntuforums.org/showthread.php?t=1523320)

So, now this "cold modem" formula stopped working last week. If I reboot into Windows XP, the ethernet light comes on. Next day, boot into linux, no ethernet! Windows yes, linux no. It worked great for weeks, then stopped. It's a live CD, no settings were changed. I even reset the modem last night..had to go back to Windows and enter the ISP password and username to get it reactivated. Reboot to Linux, ethernet light not on again. Have I repeated this more than once? Sorry!

Why can this thing work perfectly, then for no apparent reason, stop working?

Thanks for any help!

c

---

### Post by Vishnu V on 2010-08-22
Try to create a new connection and set the address netmask and gateway provided by ISP under the IPV4 settings (Method Manual and click add)

---

### Post by cracklins on 2010-08-22
I'm not sure how exactly to determine where that information is located. With my old USB connection, whether or not that had anything to do with it, in Windows XP I go to Network Connections/Properties and under TCP/IP it would list IP Address, Subnet Mask and Default Gateway. Presently, those fields are empty and a check mark is beside "obtain ip address automatically".

---

### Post by cracklins on 2010-08-22
By the way, and correct me if I'm wrong, doesn't the ethernet connection have to be available before a "new connection" can be created? In other words, if the ethernet light is not on in the modem, and the modem is not detected, and the symbol in the task bar says "connection not available", doesn't this mean as far as the operating system is concerned, there is nothing for the "new connection" to connect to? 

Is it possible I need a driver?

Then again, it worked up until a week ago, then just quit. Still works for Windows XP, but not for Linux.

---

### Post by goofynewf on 2010-08-23
I had a similar problem when I reinstalled 10.4.  I am using NBR on a Dell Mini 9.

Here is the original thread: [http://ubuntuforums.org/showthread.php?t=1558809](http://ubuntuforums.org/showthread.php?t=1558809)

It was recommended to go to:
System --> Administration --> Hardware Drivers

I also made sure I used a hard wired Internet connection to get all updates and for the drivers.  When I opened the Hardware Drivers, there were two available.  One is 'free' and the other is 'proprietary.'  I had no problem activating the free one.  I could not activate the other one.  It does not seem necessary and, after restarting, my wireless networks were available to me.
 
I hope this helps.

---

### Post by cracklins on 2010-08-25
OK, I have the answer, for now at least....until something else wacky happens.
 
Again, I'm using a Live CD with Windows XP as the native OS.

When XP shuts down, apparently it can, at it's own descretion, tweak the modem settings. These settings are saved in the modem itself, I believe. So no matter what OS is used after XP shuts down, the modem is set to however Windows XP left it. Therefore, by going into Network Connections in XP and navigating to the ethernet card settings, you can set it to "wakeup on LAN". Now when the computer shuts down, and is turned off, if the modem is still on the ethernet light remains lit. Live CD's now have a network connection and can access the internet.

---

