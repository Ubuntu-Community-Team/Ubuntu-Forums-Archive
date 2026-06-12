---
title: "lost wireless after kernel update"
date: 2006-01-10
forum: General Help
---

### Post by gatorbrit on 2006-01-10
Just did the automatic kernel update and my DLink USB wireless DL122 is no longer found by ubuntu and won't work.  Did the update write over my previous configuration in some way?

When I boot the previous kernel it works fine.

---

### Post by towsonu2003 on 2006-01-10
if you are using ndiswrapper that you compiled yourself, I believe you have to compile it again...

---

### Post by gatorbrit on 2006-01-10
Actually I was using a native linux driver rt2570.

---

### Post by danish_demon on 2006-01-24
[QUOTE=gatorbrit]Actually I was using a native linux driver rt2570.[/QUOTE]

i have the same problem, so i just went through the installation again (i deleted the rt2570 folder, untared the tar file, make, make install, insmod, etc.).  i assume there is an easier way, but i don't know what it is.

---

### Post by gatorbrit on 2006-01-26
[QUOTE=danish_demon]i have the same problem, so i just went through the installation again (i deleted the rt2570 folder, untared the tar file, make, make install, insmod, etc.).  i assume there is an easier way, but i don't know what it is.[/QUOTE]

There is an easier way, it was $39 :( at bestbuy electronics - a DWL 512 wireless pci card - that works right out of the box.  PLugged it in a slot, turned the PC on and ubuntu recognized it from the outset.  I should have gotten this one at the outset.

---

### Post by danish_demon on 2006-01-27
[QUOTE=gatorbrit]There is an easier way, it was $39 :( at bestbuy electronics - a DWL 512 wireless pci card - that works right out of the box.  PLugged it in a slot, turned the PC on and ubuntu recognized it from the outset.  I should have gotten this one at the outset.[/QUOTE]

my stupid dell laptop doesn't have a full size pci card slot; it has the "express" card slot, which best buy did not have any wireless cards for.  i imagine the only way i could get one is from dell, but i'd rather not.

---

### Post by gatorbrit on 2006-01-28
Don't get the dell wireless card - the first wireless I had was a dell usb card - I did the whole ndiswrapper thing and it was a disaster.  Dell is pretty linux unfriendly - when I ordered a pc from them I said I want to make it dual boot linux and the guy on the other end of the line said "oh you shouldn't do that - thats not a good idea at all".

---

### Post by towsonu2003 on 2006-01-28
[QUOTE=danish_demon]my stupid dell laptop doesn't have a full size pci card slot; it has the "express" card slot, which best buy did not have any wireless cards for.  i imagine the only way i could get one is from dell, but i'd rather not.[/QUOTE]
I remember seeing somewhere that there are these wireless adapters that connect to your ethernet port and don;t need extra effort in linux. but you might wanna read more about them in google.com/linux (search) bf buying. don't remember what they are called. maybe amazon.com knows? :twisted: 

there are also usb wireless thingies, but you'll need to buy a linux-supported one. :-k

PS. did the OP solve his/her wireless problem due to kernel update? if yes how?

---

### Post by g3r41d on 2006-01-31
I'd also got this prob.. How to solve it. I cant even reinstall the drivers now. Due to my upgrading my kernel. Now i cant build the wireless drivers due to the build changing from my previous kernel to the new kernel... 
Argghhh

---

### Post by towsonu2003 on 2006-01-31
[QUOTE=g3r41d]I'd also got this prob.. How to solve it. I cant even reinstall the drivers now. Due to my upgrading my kernel. Now i cant build the wireless drivers due to the build changing from my previous kernel to the new kernel... 
Argghhh[/QUOTE]
don't know how they work but, you could use the old kernel. it should be in the grub menu (the list of kernels and operating systems that comes up right after booting). if you don't see a list, I think you can see it using esc key. 

Also, **file a bug report**. 

I started to believe that updating the kernel should cause some kind of popup window to tell the users that this may screw up compiled stuff. 

If you compiled your drivers, you will have to recompile them with the new kernel. make sure you have packages build-essential and linux-headers-`uname -r` (output of command "uname -r"). they are apt-gettable and in the installation cd. 

I think danish-demon knows the solution of this as s/he is saying: 
> i have the same problem, so i just went through the installation again (i deleted the rt2570 folder, untared the tar file, make, make install, insmod, etc.). i assume there is an easier way, but i don't know what it is.
the ubuntu-ish of what s/he's saying is that s/he recompiled the drivers while using the new kernel.

---

### Post by danish_demon on 2006-01-31
[QUOTE=towsonu2003]don't know how they work but, you could use the old kernel. it should be in the grub menu (the list of kernels and operating systems that comes up right after booting). if you don't see a list, I think you can see it using esc key. 

Also, file a bug report. I started to believe that updating the kernel should cause some kind of popup window to tell the users that this may screw up compiled stuff. 

If you compiled your drivers, you will have to recompile them with the new kernel. make sure you have packages build-essential and linux-headers-`uname -r` (output of command "uname -r"). they are apt-gettable and in the installation cd. 

I think danish-demon knows the solution of this as s/he is saying: 

the ubuntu-ish of what s/he's saying is that s/he recompiled the drivers while using the new kernel.[/QUOTE]

thanks for making me look smarter than i actual feel for once around here :)

---

### Post by Algot Runeman on 2006-01-31
Similar experience with Netgear WG511T card that worked just great with 5.04 through all its updates.
[Toshiba Satellite w/Celeron processor]
First tried to install the 5.10 upgrade over the 5.04. The card didn't work.
Then did a fresh 5.10 install from CD. Better result, but still not really right.
After reboot, the card works, picking up DHCP address and then runs for up to 15 minutes. Then the connection is dropped.
I have deactivated and reactivated the card several times. No effect.
Machine will not do a restart, either, that it would do with 5.04. I only am able to do a shut down and then cold start. After cold start, the WG511T works again for 10-15 minutes and then dies again.

---

