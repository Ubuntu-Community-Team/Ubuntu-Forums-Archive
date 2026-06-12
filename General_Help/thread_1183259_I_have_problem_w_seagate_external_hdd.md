---
title: "I have problem w/ seagate external hdd"
date: 2009-06-09
forum: General Help
---

### Post by khoacao on 2009-06-09
Hi guys, I'm new here so please help me out!!!

I just bought a 1TB seagate freeagent, it's a 2.0 USB, appears well on my 7.04 ubuntu (I know, it's really old, and for some reason I need your help since it could not update). 

For my Seagate, the icon is on the desktop, I can view it and everything, but when come to copy and paste, as simple as an image from my hard drive, it says that my drive is "read only."

About my old operating system, I have used this version for about half a year now without any incident besides that updating things. When I selected Updates, it runs for a while looking like downloading files from the main directory, but then came to a stop where it said the directories that were needed were unable to retrieve or were deleted. So I have stuck with the old version. Just FYI, my comp can't run on 8.4 either, some issues with the graphic requirements, so I would like to know any long term supported version that is any safer than the version i'm using. I'm actually in love with this version, but afraid that being unable to update is A LITTLE BIT unsafe.
Thanks all.

---

### Post by sendblink23 on 2009-06-10
If the USB External Hard Drive is Mounted

simply open Terminal and Execute: sudo nautilus

And you should be able to work with it *NOTE* Don't close the Pop Up Window that appears after that command, once its closed you would be exited from Mr. Judo Chop (nautilus command)  =P

good luck in that

Also this is only needed if your keeping that HD as a Windows Readable NFTS,  but if you want it Linux only that HD... format it to ext3  and you should b perfectly fine (will not work under windows)

As of other Linux Distro...  no idea... I would sugget BackUp everything to that hard drive ..  and burn many different versions of Linux Flavors: xubuntu, kubuntu, linuxmint, puppylinux, opeSuse, Archlinux, blahh so many flavors to eat its like Baskin Robins Linux Ice Cream Shop

---

### Post by Nevart on 2009-06-10
I have one of these drives connected right now and it is working fine.  Sometimes they go a bit funny and you can fix it by unplugging the power from the drive and unplugging the USB cable, then plug it all back in again (power first, then USB).  There is a good chance that the drive will be detected and auto-mounted.

An exception might be if you reformatted the drive with some weird file system.  Then Ubuntu might not recognize it as a removable drive and would probably not auto-mount it.

---

