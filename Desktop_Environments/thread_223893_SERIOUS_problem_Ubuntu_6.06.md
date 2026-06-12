---
title: "SERIOUS problem Ubuntu 6.06"
date: 2006-07-27
forum: Desktop Environments
---

### Post by jliakos on 2006-07-27
Hello. I have a pc with GIGABYTE K8NF-9 motherboard, AMD 3200+ CPU. I've successfully installed Ubuntu 6.06 desktop 32-bit. When I removed the Logitech wireless mouse and replaced it with Microsoft optical mouse, when i logged in the pc shutted  down! This happens every time i try to log in... I've tried to format the HD and re install Ubuntu but the same problems exists!!! I cannot even install Ubuntu from scratch... I don't know if the problem occurs because of the Microsoft mouse or not, beacause I have no problem in Windows XP. (The Microsoft mouse is plugged in PS2 with an usb-to-ps2 adaptor). Any suggestions acceptable.. Thanks!

---

### Post by philippe_carlo on 2006-07-27
Replace the mouse?

Not really a fan of those solutions, but since the mouse says 'microsoft', it changes the prespective ;-) Maybe there is something like a 'microsoft ps2 implementation' that get your computer confused, or maybe it's just broken.

You may also want to look in the log files for strange things.

---

### Post by jliakos on 2006-07-27
The Microsoft mouse is not broken... It works perfectly in Windows XP and in live CDs like Knoppix... I have seen the log files ie /var/log/messages but there is nothing strange there... :(

---

### Post by bullgr on 2006-07-27
vale allo pontiki re patrida min trelenesai...
ase pou den prepei na einai to pontiki...
kai ego exo microsoft

---

### Post by frodon on 2006-07-27
This is an english forum, please answer in english.

jliakos, maybe your mouse is just not supported by ubuntu, perform a forum search with the name of your mouse to see if other users got the same problem with this mouse.

---

### Post by jliakos on 2006-07-27
file mou exo dokimasei na ksanavalo to logitech alla pali ta idia... ti skata exei pathei den ksero. To koulo einai oti tin proti fora to eixa valei kanonika xoris kanena provlima molis egine afti i allagi....ta epaikse entelos

---

### Post by go2dell on 2006-07-27
There's no particular reason the Microsoft mouse shouldn't work with your motherboard, unless the mouse is faulty.  Since you seem to be having trouble with two different mice, you either have two bad mice or there's a different problem. ;)

Since you say you can boot under Windows with that mouse attached, I'm guessing it's not a problem with the mouse.  I'm wondering why you are connecting a USB mouse with a PS/2 adapter.  Perhaps you're using all your USB ports for other things?  In any case, you should probably unplug absolutely everything not needed to get your system to boot.  Leave the monitor, mouse, and keyboard connected.  Speakers, printers, and anything else should be disconnected.

Then try booting again.  If it's successful, add one device at a time until you get a system that doesn't boot, and then you'll know the cause of the problem.  If it still won't boot with a minimal configuration, unplug the mouse (you don't need it to boot) and try it again.  If that's the case, you may have an problem somewhere inside the box, which is a horse of a different color to solve. :rolleyes:

---

### Post by jliakos on 2006-07-27
Thanks I will Try it in the evening and see what happens.. I am at work now :)

---

### Post by jliakos on 2006-07-28
Did not work!! I tried everything i plugged in only keyboard and mouse in ps2, only keyboard, keyboard in usb mouse in ps2, mouse in usb keyboard in ps2 but the problem insists. I insert the install CD and I cannot even see the gnome desktop from where I start the installation :(

---

### Post by frup on 2006-07-28
what video card do you have? or do you have intergrated gfx or what?

how far in to boot do you get?

---

### Post by jliakos on 2006-07-28
I have ATI 3D Club X550 ,a soundblaster audigy sound card and onother one on board. I insert the Ubuntu install CD and as it tries to load gnome desktop it shuts down...I cannot even install it :(

---

### Post by cotcot on 2006-07-28
As you are able to install 6.06 i guess your mouse works with the installCD. You can install from the CD untill reboot and then nothing. Have you tried the Alternate installCD ?

---

### Post by jliakos on 2006-07-28
No I cannot install Ubuntu. The thing is the first time I managed to install it but then this problem occured. Then i tried all the solutions mentioned before and then I formatted the hd. Now I cannot install :(

---

### Post by h2gofast on 2006-07-28
I have ubuntu on two pcs and both work with microsoft optical mouses.  
And your mouse works in windows, so it isn't the mouse.
You say the livecd works, does it work everytime, and does it recognize the MS mouse everytime?  If it works once, it will work again.
How far into the install do you get?
When it did bootup, Exactly where did it fail and what did it do.  Does the computer lock up, i.e. screen freezes and accepts no input from keyboard or mouse.  Or does it shutdown like someone pulled the plug, or does it shutdown like it would if you clicked on the shutdown button in the logoff menu?

---

### Post by jliakos on 2006-07-28
> **h2gofast said:**
> I have ubuntu on two pcs and both work with microsoft optical mouses.  
And your mouse works in windows, so it isn't the mouse.
You say the livecd works, does it work everytime, and does it recognize the MS mouse everytime?  If it works once, it will work again.
How far into the install do you get?
When it did bootup, Exactly where did it fail and what did it do.  Does the computer lock up, i.e. screen freezes and accepts no input from keyboard or mouse.  Or does it shutdown like someone pulled the plug, or does it shutdown like it would if you clicked on the shutdown button in the logoff menu?

I select install Ubuntu... it loads the necessary drivers and then tries to load gnome desktop ...When u think the gnome desktop will load then it shuts down like someone pulled the plug. I manage to see the desktop backround and the it shuts down

---

### Post by h2gofast on 2006-07-28
> I select install Ubuntu... it loads the necessary drivers and then tries to load gnome desktop ...When u think the gnome desktop will load then it shuts down like someone pulled the plug. I manage to see the desktop backround and the it shuts down

So it doesn't do this with the logitech mouse?  At this point I don't know if I can help you.  That doesn't mean the problem cannot be solved.  But this is what I would do.
Go to [www.google.com/linux](www.google.com/linux) and do a search for the exact model of the motherboard you have and add words like "crash" or "shutdown".

Also, and this might be the easiest route, go ahead and install with the logitech mouse.  
Then "sudo aptitude update && aptitude dist-upgrade"   
If something is buggy, maybe it's been taken care of since the release.
Then plugin the microsoft mouse and "sudo dpkg-reconfigure xserver-xorg"



You say that it runs fine under windowsXP, so that tells us that the hardware is not broken, which is good.  Sometimes certain combinations of motherboards and hardware creates a bad voodoo that just won't play nice.  Sounds weird but its the only way I know how to explain it without a programmer involved, which I am not.  


If that doesn't work I'm not sure where to go next.
Cheers, and let us know if you get it working or not.

---

### Post by jliakos on 2006-07-28
> **h2gofast said:**
> So it doesn't do this with the logitech mouse?  At this point I don't know if I can help you.  That doesn't mean the problem cannot be solved.  But this is what I would do.
Go to [www.google.com/linux](www.google.com/linux) and do a search for the exact model of the motherboard you have and add words like "crash" or "shutdown".

Also, and this might be the easiest route, go ahead and install with the logitech mouse.  
Then "sudo aptitude update && aptitude dist-upgrade"   
If something is buggy, maybe it's been taken care of since the release.
Then plugin the microsoft mouse and "sudo dpkg-reconfigure xserver-xorg"



You say that it runs fine under windowsXP, so that tells us that the hardware is not broken, which is good.  Sometimes certain combinations of motherboards and hardware creates a bad voodoo that just won't play nice.  Sounds weird but its the only way I know how to explain it without a programmer involved, which I am not.  


If that doesn't work I'm not sure where to go next.
Cheers, and let us know if you get it working or not.

Thanks for the hints but i cannot install even with logitech mouse...

---

### Post by jliakos on 2006-07-28
If anyone has the GIGABYTE K8NF9 with latest bios F11 please confirm he has succesfully installed ubuntu

---

### Post by Tomosaur on 2006-07-28
Given the awkward point where this hangs, it could be a range of problems, since the system still hasn't booted up fully yet. It could be a problem with X, or GNOME, or Nautilus, or anything. Your best bet for now is probably to choose the 'check CD for defects' option when you first boot from the CD.

I would also recommend you ditch the USB/PS2 adaptor, and just opt for a USB hub instead, since this could possibly be causing problems anyway.

I am also using an optical mouse and wireless keyboard (HP), without any problems at all, which is why I believe this to be a problem with your actual install CD rather than Ubuntu.

---

### Post by jliakos on 2006-07-31
> **Tomosaur said:**
> Given the awkward point where this hangs, it could be a range of problems, since the system still hasn't booted up fully yet. It could be a problem with X, or GNOME, or Nautilus, or anything. Your best bet for now is probably to choose the 'check CD for defects' option when you first boot from the CD.

I would also recommend you ditch the USB/PS2 adaptor, and just opt for a USB hub instead, since this could possibly be causing problems anyway.

I am also using an optical mouse and wireless keyboard (HP), without any problems at all, which is why I believe this to be a problem with your actual install CD rather than Ubuntu.
Check CD for defects returned no errors...I updated the bios too and see what happens!

---

### Post by jliakos on 2006-07-31
> **jliakos said:**
> Check CD for defects returned no errors...I updated the bios too and see what happens!
I see there is an IRQ 11 conflict --nvidia with sata drive. Maybe this may causing all my problems?? How can i resolve this ?

---

### Post by go2dell on 2006-08-01
It is likely not a conflict.  On modern motherboards, especially since the advent of "everything on board" motherboards, there just aren't enough IRQs to support everything, so they share IRQs around to some devices.

If you really do think it's causing a problem, many motherboards (though not all) will allow you to force IRQs in the BIOS.  Before you start shifting devices to different IRQs, you might try to free up a few.  For instance, are you using your serial ports?  What about your parallel port?  That makes three potential free IRQs that you could move to other devices simply by turning off those ports.

Other motherboards require you to physically move devices around in order to change the IRQ assignment, meaning that built-in devices are stuck with whatever IRQ the brilliant designers intended.  If your board is one of these, you're likely out of luck.

---

### Post by ethan961 on 2006-08-01
Could this be an overheating problem? Did you notice anything else abnormal? Maybe this is a problem with the kernel controlling the power supply incorrectly. I highly reccomend trying the alternate install cd. Has anything odd happened to Windows?:-k  Hope I can help.;-

---

### Post by jliakos on 2006-08-21
Hello I am back from my vacations. I updated the bios and the problem was solved! I do not know how to explain it but it is true. Thanks for the help all of you!

---

### Post by go2dell on 2006-08-22
Ah, the magical BIOS upgrade fix.  Sad, but true:  there are lots of broken BIOSes out there, and we are all at the mercy of the manufacturers to have a working computer.  It's a case of hit or miss; sometimes the upgrade helps, but sometimes it hurts.  Glad to know that your upgrade fixed everything! \\:D/

---

