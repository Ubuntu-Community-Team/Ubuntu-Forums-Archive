---
title: "Backtrack- VBOX or live CD ?"
date: 2011-06-16
forum: Desktop Environments
---

### Post by supergreatbirdman on 2011-06-16
Hi i am an Ubuntu 10.10 user and would like to explore some of the tools in Backtrack and understand that improper use can cause damage to my pc.  That said, is it better to install in VBOX, or download an iso, burn to CD and run that way?  
Does it matter?
Any preferences?
Thanks

---

### Post by Mr.Dee on 2011-06-16
Should not make a difference.  Just don't run all kinds of crazy commands to your machine's folders (i'm guessing windows) when you boot up a live cd.  Of course vbox is pretty safe and I guess more contained, but overall the live cd or vbox should be ok.  I've used both methods for over a year and have not had any problems.  I prefer booting from a usb or sd card, I think it runs faster.  I find myself booting up BT in vbox if I ever need to surf the web for anything that might be mildy dicey.  For example, if I feel like researching a security tool and am using my windows machine I will boot up in vbox just because it is handy. As a bonus if I'm browsing with the firefox version that comes with BT, it is set on paranoid mode and will ask you for permission before executing any code from the webs.

---

### Post by supergreatbirdman on 2011-06-17
Hey so I chose to download the iso.  
	
Flavor:	GNOME
Arch:	32 bit
Image:	ISO

i copied the md5sum command on the Backtrack Wiki site to check the validity of the iso.

md5sum bt5-kde-32.iso
command not found.

makes sense given that i downloaded a gnome version, but changing "kde" to "gnome" had no effect.  Matching the capitols of the actual file name also had no effect.  It seems skipping this step would be unwise.  Any help?

---

### Post by supergreatbirdman on 2011-06-18
So I am not sure what I was doing wrong before but I got md5sum to work

cd Downloads

md5sum BT5-GNOME-32.iso

cheers

---

