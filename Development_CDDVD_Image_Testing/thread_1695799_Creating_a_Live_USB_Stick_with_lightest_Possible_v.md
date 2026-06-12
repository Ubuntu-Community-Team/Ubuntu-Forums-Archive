---
title: "Creating a Live USB Stick with lightest Possible version of ubuntu."
date: 2011-02-26
forum: Development CD/DVD Image Testing
---

### Post by jeetendra.choudhary on 2011-02-26
Hi All,

The idea is to create a plug and play Operating system Usb Disk in which one can work and store the data as well. Means the host system will provide the RAM and Processor to work and all the storage will be of the guest Operating system. 

I know this idea is one of the old experiments but my point is how stable it is for regular work I mean is it possible that i can work in such setup for one project (ya i am a developer and project means mid size development project which will require all sort of development tools like eclips, java sdk and so on and on..) and after each such project I'll do the necessary clean-up.

Which ubuntu version i should use (means in which i'll get more stability and support if required, same should be the lightest and smallest too.)

What and all software should be used in order to comply with the requirement and system stability.

Any suggestions and solution would be great help.

Thanks & Regards
Jeetendra

---

### Post by sikander3786 on 2011-02-26
I think you might find this easier.

[http://ubuntu4beginners.blogspot.com/2011/02/portable-ubuntu-persistent-usb-using.html](http://ubuntu4beginners.blogspot.com/2011/02/portable-ubuntu-persistent-usb-using.html)

---

### Post by jeetendra.choudhary on 2011-02-27
Hi Sikander,

Thanks for your reply its helpful but my requirement is slightly different.

1. I don't want to use Vbox as i don't want to use any of the feature of the host system in such case it doesn't seems like good idea to use a windows system and Vbox inside that.

2. If i will use Vbox the host system will consume the RAM lets say half of it if the host system will have 2 gb of RAM then guest system can use only 1GB which will not be sufficient for development related work.

Is there any idea to boot the system directly from the USB and use it as a host OS so that the guest OS can use all available system resources fully.

Thanks & Regards
Jeetendra

---

### Post by sikander3786 on 2011-02-27
I think it won't be possible to run an Operating System within another one without using Virtualization.

With Ubuntu as you know, you can do a full install on-to a USB drive and use it as a normal HDD but still, you need to do a cold boot and on a single PC, a single OS can run at a time.

If a Guest OS is running inside a Host OS (if Virtualization or what-ever you think is possible), the Host would still be definitely using the resources as well the Guest OS.

---

### Post by foxmuldr on 2011-03-02
> **jeetendra.choudhary said:**
> 
Is there any idea to boot the system directly from the USB and use it as a host OS so that the guest OS can use all available system resources fully.

Thanks & Regards
Jeetendra

What you're asking for is not possible due to the requirements of the hypervisor. While it could boot and run from a USB stick, it would not be fast or efficient, and would still consume large resources to be able to run any OS, which means virtualizing hardware ports and devices.

It would be possible to do as a doctoral thesis for proof of concept. But for commercial app, unlikely to be viable.

- Rick C. Hodgin

---

### Post by julianb on 2011-04-28
I'm still trying to figure out what it is you want. When you create a really clear description of what you want, it'll be easier to figure out what tools have to be put together and/or created.

it sounds like you want 
1. a usb stick that runs a host operating system
2. the computer with its on-the-hard-drive OS should be booted as a guest operating system(?), but changes should not be made to the hard drive contents, (easy enough) AND documents should be saved to the USB stick (easy enough) and maybe settings for use with the "guest OS" on the hard drive should be saved to the USB stick (very problematic)

why would you want this?

Now, if you want an OS that does not waste RAM or processor cycles, and can be either a guest or host for virtualization, you can consider Tiny Core Linux. But to be honest you might find it easier to do what you want by simply running one OS at a time.

You aren't wanting to seamlessly transfer a running operating system into being a "guest OS" are you?

---

