---
title: "system is really slow after upgrade"
date: 2009-05-28
forum: General Help
---

### Post by scottdky on 2009-05-28
Hi,

After upgrading from hardy (8.04) to jaunty (9.04) (via two upgrade steps), I now have severe CPU overload problems, when running an IDE such as Eclipse and Firefox. I have tried switching to Netbeans & Firefox, but the CPU is still taken up. If I run "top", half of the CPU will be taken up by either Java (when running Netbeans) or Xorg. 

I have searched the forums, and this problem seems to be a common one, but without any real answers. Right now, my system is virtually unusable. Every little operation in Netbeans sends the CPU to 100%. Ditto with Eclipse. I upgraded Eclipse to the latest before switching to Netbeans, and I believe I am using Java6?

Xorg appears to be the most likely culprit (I can have severe slowdowns just running Firefox), although I have heard Firefox may cause the same problems. As I type this message, the CPU will either be low or at 100% for almost a minute at a time with Xorg getting 60%. If I don't run Netbeans or Eclipse, the problem seems not so severe.

Does anyone know how to track this problem down?

Thanks,
Scott

---

### Post by cwmoser on 2009-05-28
Don't have enough information to fully tackle this.

I would try:  1) disable ipv6, 2) install preload,  and 3) turn off Compiz

Turn off ipv6:

IPv6 Quick (Firefox) Fix

If you can't access the web through Firefox, though you know you have an internet connection via your modem/router try the following:

Enter about:config in Firefox's address field.

Enter ipv6 in the new Filter: field.

Double click on the line left in the display window to change it's boolean value to true.

Restart Firefox.

& that should be that...  

____________________


Disable IPv6 Globally

Unlike the method of editing /etc/modprobe.d/aliases, the following method does not run the risk of being overwritten. 

Do the following to disable IPv6 globally:

1. To verify that the IPv6 module is loaded type the following from a terminal:

handy@birdfish:~$ lsmod | grep ipv6
ipv6 265856 10

2. Then from a terminal type:

handy@birdfish:~$ sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

3. Restart

4. To verify that the IPv6 module is not loaded type the following from a terminal:

$ lsmod | grep ipv6


If for whatever reason the above method does not work, type sudo nano -w /etc/modprobe.d/blacklist & enter the line blacklist-ipv6, then do steps 3. & 4. as above.





Install preload:

sudo apt-get install preload

---

### Post by Steelmourne on 2009-05-28
What CPU do you have and have you installed updated drivers?

---

### Post by QIII on 2009-05-28
Are you seeing an obscene usage of system memory as well?

Xorg reopened a bug that had been closed (can anyone say "regression") having to do with a serious memory leak in the latest version under certain conditions.

I noticed it after having started using Netbeans 6.7 beta.

If you are running an ATI driver, you may want to check out

[https://bugs.launchpad.net/ubuntu/+bug/353800/comments/20](https://bugs.launchpad.net/ubuntu/+bug/353800/comments/20)

I'm not going to say that the post is definitive, and you should always be careful about doing anything described in posts like that.  I'd do some research to see if you can find other similar methods that confirm validity.

I've heard all sorts of horror stories about manually installing video drivers.

---

### Post by scottdky on 2009-05-28
1) Are you seeing an obscene usage of system memory as well?

No memory is about 50% to 3/4ths used. I have 1.2 Gig installed.

2) What CPU do you have and have you installed updated drivers? 

I have tried updating the system (I only just installed it about a week ago), but there seems to be an error having to do with invalid certificates that makes me wonder if the system update is working anymore. Here is the CPU info:

```
System Information
	Manufacturer: Dell Computer Corporation
	Product Name: Dimension 3000               
	Version: Not Specified
	Serial Number: 3N66S71
	UUID: 44454C4C-4E00-1036-8036-B3C04F533731
	Wake-up Type: Power Switch

Handle 0x0200, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Dell Computer Corp.
	Product Name: 0K8980
	Version:    
	Serial Number: ..CN70821522A132.

Processor Information
	Socket Designation: Microprocessor
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel
	External Clock: 533 MHz
	Max Speed: 3600 MHz
	Current Speed: 2400 MHz
```

```
Graphics:
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```

I have disabled ipv6 in Firefox, but I don't think that was my problem.
I have also installed preload, but it doesn't seem to have helped.
I don't know what compiz is or how to disable it. A half hour searching on the web failed to yield relevant info. Do I even have it? How can I tell?

When I first noticed the problem, I disabled some gadget called tracker. That helped quite a bit. It seems like everything seems to really bog the system down, not just one thing, although I can't rule out Firefox since it is a constant in my daily use, but it seems okay by itself with other small apps.

---

### Post by QIII on 2009-05-28
Intel graphics?

dmizer has some good advice in this thread:

[http://ubuntuforums.org/showthread.php?t=1171981&highlight=intel](http://ubuntuforums.org/showthread.php?t=1171981&highlight=intel)

---

### Post by scottdky on 2009-05-29
> **QIII said:**
> Intel graphics?

dmizer has some good advice in this thread:

[http://ubuntuforums.org/showthread.php?t=1171981&highlight=intel](http://ubuntuforums.org/showthread.php?t=1171981&highlight=intel)

That did it! I knew I wasn't going crazy. The system seems to work fine now. I had to close Firefox, but did not even reboot. I seem to be able to edit in NetBeans and even debug without any substantial slowdowns. What a difference - I couldn't hardly even scroll or type before.

Thanks so much for everyone's help. Hopefully this message will be found by others with the same problem. I love Ubuntu and all its great support.

Scott :D

---

