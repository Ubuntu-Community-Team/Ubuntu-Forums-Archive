---
title: "Unable to access my CD drive from Ubuntu."
date: 2009-04-04
forum: Desktop Environments
---

### Post by radhakrishna.commerce on 2009-04-04
I installed Ubuntu 8.10 on my Desktop a month ago. I've just realized that Ubuntu does not recognize my CDRW/DVD drive. 

I Installed Ubuntu from within my other OS, Windows 2000. 

I am able to access the CDRW/DVD drive from Windows though.

I checked fstab and I don't see an entry for the CD drive at all. Below are the entries in my fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/home.disk /home           ext3    loop            0       2
/host/ubuntu/disks/usr.disk /usr            ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```

Also attached is the output of "sudo lshw.txt". This too does not show up the CD drive.

How do I fix this issue?

I searched in the forums and I did find some bugs related to this, however these were raised almost a year ago. I wonder if a fix  is available.

---

### Post by itix on 2009-04-05
I have never installed ubuntu from windows, but I must say that your fstab looks really wierd... /host/ubuntu => what the hell??

---

### Post by radhakrishna.commerce on 2009-04-05
Could the "weird" entries in fstab be a problem?

---

### Post by itix on 2009-04-06
To be honest, I don't know. It seams that your folder structure is a bit different than what I am used to. Your disks are a bit oddly mounted but since the system boots, then everything is probably fine. Someone with more windows install experience than me could probably tell you if [COLOR="Green"]fstab[/COLOR] is supposed to look like that.

Do you have a device called [COLOR="Green"]scd0[/COLOR] in your folder [COLOR="Green"]/dev[/COLOR]?

You can check that by navigating to the root folder ("[COLOR="Green"]/[/COLOR]") in the file browser and then search through the [COLOR="Green"]dev[/COLOR]-folder, or by executing the command [COLOR="Green"]ls /dev | grep scd0[/COLOR].

---

### Post by radhakrishna.commerce on 2009-04-06
Thank you for your reply.

> Do you have a device called scd0 in your folder /dev?
No. This was one of the first things I checked. The CDRW/DVD device just does not appear anywhere.

However, I do see a directory called /media/cdrom0, but, I guess, that's not my CD. Because one of the things I tried was to insert a CD and access /media/cdrom0 and nothing shows up.

---

### Post by itix on 2009-04-06
No, the folder /media/cdrom0 does not necessarily mean that you have a CD-drive (or that Ubuntu has detected one).

Your hardware check seamed to reveal nothing that would give a hint of detection.

I assume that you can access the CD-drive from windows?

---

### Post by radhakrishna.commerce on 2009-04-06
> I assume that you can access the CD-drive from windows? 
Yes. And that's what stumps me.

Ubuntu is able to access USB drives with no problems at all.

Could this be a hardware problem?

---

### Post by itix on 2009-04-06
If windows can use it, no.

This is probably due to the fact that the kernel has no driver for the CD-drive. There might be a possibility that there is no driver at all. It would be of great help if you knew the manufacturer.

---

### Post by radhakrishna.commerce on 2009-04-06
My motherboard is Intel-915S. My CD-drive is a Samsung make.

---

### Post by itix on 2009-04-06
I noticed the motherboard in the LSHW-file.

This is what I could find in the hardware libraries. Do you recognize any of these?

[http://ubuntuhcl.org/browse/search?offset=0&category=19&manufacturer=235&os=&order-by=&keywords=](http://ubuntuhcl.org/browse/search?offset=0&category=19&manufacturer=235&os=&order-by=&keywords=)
[http://www.linuxquestions.org/hcl/showcat.php/cat/354](http://www.linuxquestions.org/hcl/showcat.php/cat/354)

---

### Post by radhakrishna.commerce on 2009-04-06
I am at work now and don't know the exact make. Will let you know once I reach home.

Thanks for all your replies. They are very helpful.

---

### Post by radhakrishna.commerce on 2009-04-06
Thank you for being so patient. My CD is a Samsung OctoEDGE TSSTcorp CDW/DVD SH-M522C.

It is not listed in either of the sites.

I'll try and find the driver for this CD-Drive.

---

