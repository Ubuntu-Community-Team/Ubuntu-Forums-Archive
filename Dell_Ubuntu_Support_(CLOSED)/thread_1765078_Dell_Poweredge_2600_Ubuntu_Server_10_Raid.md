---
title: "Dell Poweredge 2600 Ubuntu Server 10 Raid"
date: 2011-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jcdudc on 2011-05-22
Installing Ubuntu server 10 as sole operating systemon dell Poweredge 2600 configured in raid 5 (was working perfectly in Win Server 03).  Have three drives at 36 GB and 3 at 146 GB.

Followed instructions from Ubuntu Server Guide 4.1 Advanced Install Raid and cannot complete install - cannot select/change "Bootable flag: off"  

Have tried  'F6 - Other options' and selected  the no dmraid options.  Still no joy.  By NO MEANS a Raid expert but seems bios or raid controller are "showing" the the 6 drives as two and dmraid does not recognize it???

---

### Post by jcdudc on 2011-05-25
anyone help?

---

### Post by jcdudc on 2011-05-26
can anyone direct me to some source of info?  do NOT want to go back to Windows

---

### Post by novafluxx on 2011-05-29
First, check what hardware you have. That server most likely has a hardware RAID controller. Its probably a PERC3 or PERC4.

You'll want to configure the RAID array using the controller, not using software/the OS.

---

### Post by jcdudc on 2011-05-29
Perc 4/Di raid. I configured via software at boot ctrl-m

---

### Post by novafluxx on 2011-05-29
You could always speak with Dell technical support. They do have an alternate OS queue. That server also should have lifetime tech support. You can call them at 1-800-822-8965 (USA & Canada).

So after configuring the logical disks through the controller, Ubuntu still shows you all of the physical drives?

---

### Post by jcdudc on 2011-05-29
disk partition indicates only two drives - not six, last picture in original post.  it's like the controller "fooled" Ubuntu into thinking there were only two drives

---

### Post by novafluxx on 2011-05-29
How do you have the RAID configured? How many physical drives, and how are they configured for RAID?

I see in your original post you have three drives at 36 GB and 3 at 146 GB. Are thay all configured to be 1 RAID 5 array?

---

### Post by jcdudc on 2011-05-29
Wrong reply: during the partition part of install it's like the raid controller has "fooled" Ubuntu into seeing only two drives in lieu of the six, see last picture in original posting.

---

### Post by jcdudc on 2011-05-29
have two arrays both in raid 5

---

### Post by novafluxx on 2011-05-29
Then that is why Ubuntu only sees 2 drives. The controller in essense "hides" the physical drives from the operating system, and only presents to it the logical volumes, or the RAID arrays.

In this case, 2 RAID 5 arrays! :-)

---

### Post by jcdudc on 2011-05-29
how do i change that?

---

### Post by novafluxx on 2011-05-29
What are you wanting to change? Do you not want them configured in a RAID at all?

---

### Post by jcdudc on 2011-05-29
In one of my install attempts I partitioned and continued the install as though there were only two drives - install completed but with so many errors was afraid to proceed.

---

### Post by jcdudc on 2011-05-29
I wanted to setup in raid 5 with operating system on first array and data on second.  have been running win 03 terminal server in this configuration.  Never had a failure so don't how it would have recovered but was recommendation of friend who is IT by background instead of a rookie like me.

---

### Post by novafluxx on 2011-05-29
My suggestion is to go back into the controller and delete the current configuration (BACK UP ANY DATA YOU HAVE ON THERE FIRST) then recreate the RAID 5 arrays.

Also, in the controller:

Go to objects->physical disk->starting with the first drive you see on the list press F2 and it will show you the drive properties, at the bottom of that window is the device errors. Check each drive and see if there are any errors.

Make sure you don't delete the array's before you get your data off. I'm assuming you don't have any data on them currently.

After you recreate the array's wait for them to initialize, it may take some time, let this process continue until its completed on both array's.

---

### Post by jcdudc on 2011-05-29
working on it now

---

### Post by jcdudc on 2011-05-29
done - but on initialization indicates "This Logical Drive is in Background Initialization State It cannot be selected for desired operation"

---

### Post by jcdudc on 2011-05-29
running consistancey check now - looks like it's going to be some time finishing.  

I REALLY appreciate the help.  will post tomorrow on how it proceeds.

Thanks agian

---

### Post by novafluxx on 2011-05-29
OK, let it finish its tasks in the controller. Also, did you check for any errors on the physical drives?

No problem. I will check back with you tomorrow. Lets get this resolved!

---

### Post by jcdudc on 2011-05-29
No device errors - integraty test STILL running 70% on large drive/array

---

### Post by novafluxx on 2011-05-29
It's been about an hour; does it seem to be progressing beyond that 70% mark?

---

### Post by novafluxx on 2011-05-30
Any update?

---

### Post by jcdudc on 2011-05-30
all disk are in good shape and passed consistency test. how should i proceed

---

### Post by jcdudc on 2011-05-30
Have restarted the install and in initial screen F6 no dmraid selected but during install the screen update indicates retrieving  dmraid-deb?

---

### Post by novafluxx on 2011-05-31
I think what you may be doing is telling the installer you want to setup a software RAID, which you don't want to do seeing as you have a hardware RAID controller.

Try doing a normal install, avoid anything that says RAID, and install Ubuntu as you normally would.

---

### Post by jcdudc on 2011-05-31
Done - installation went without an issue.  Use guided partition.  On boot no luck - just a blinking cursor. No directory no nothing.  Have found one thread where someone ended up selling the server because couldn't get it working - don't have that option.  Any thoughts?

---

### Post by jcdudc on 2011-05-31
Desperation - tried install Desktop Ubuntu 10.4 and it WORKED.  Can I add any of the components from Ubuntu server and use it for an application server?

---

### Post by jcdudc on 2011-06-02
End of saga.... Went back on more time and did manual install ubuntu server 10.4 with ONLY application server installed. worked but had a few errors on reboot.  Did update to version 11 and everything appears to be working properly.   closing thread  

thanks for the help

---

### Post by novafluxx on 2011-06-04
I'm not sure what happened there. May be a bug for that LSI controller driver in 11.04.

Glad you got it working!

---

