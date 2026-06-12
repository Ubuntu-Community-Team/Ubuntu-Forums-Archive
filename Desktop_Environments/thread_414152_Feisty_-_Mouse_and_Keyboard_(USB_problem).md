---
title: "Feisty - Mouse and Keyboard (USB problem?)"
date: 2007-04-19
forum: Desktop Environments
---

### Post by LinkRJH on 2007-04-19
Hi,

I just finished installing Feisty and not long after each boot my mouse and keyboard stop working.  Typically first the mouse, then the keyboard.  The mouse will freeze in whatever location it is in and the keyboard will hold doa key while I am typing and leave it held down indefinitely, no other key working.

When I disconnect and reconnect the devices they simply aren't recognized and do not work at all.

Where might my problem lie?

Thanks in advance,

Richard Hertzog

---

### Post by LinkRJH on 2007-04-19
I would appreciate any help.  I'm currently running Windows now because I am unable to do absolutely anything without being able to use a keyboard or mouse.

---

### Post by LinkRJH on 2007-04-19
Could it possibly be a USB problem?  And if so, how do I find/correct that?

---

### Post by Magiczero on 2007-04-19
Hi  

It very well could be a driver issue.  What wireless mouse are you using?  

Another thing I might try is hooking up a different mouse!

---

### Post by db9s on 2007-04-19
same problem here! Keyboard's multimedia keys get disabled. There's so many bugs even the final version. and sometimes keys keep repeating like tttttttttttttttttttttttttttttttttttthis. Its almost like this stuff gets worse as we move on

---

### Post by LinkRJH on 2007-04-20
> **db9s said:**
> same problem here! Keyboard's multimedia keys get disabled. There's so many bugs even the final version. and sometimes keys keep repeating like tttttttttttttttttttttttttttttttttttthis. Its almost like this stuff gets worse as we move on

This is the exact problem I am getting.  It's just a regular Dell mouse and Dell keyboard that came with my computer.  I don't even have multimedia buttons, they are very regular and plain.  The repeating a letter thing is just that it freezes when you are typing that letter and continues to hold it down.  I've had it happen several times now and am just using a Windows partition since I have absolutely no method of controlling anything when I am in the Ubuntu one.

---

### Post by zykris on 2007-04-22
Hi,
I just installed Feisty today and I am having the same problem as well. It hangs at random times without any warning or a specific sequence. This happened before in edgy but i just had 2 unplug the keyboard or mouse and re-plug it back and it usually works but not this time.

Also, the keyboard issue keeps popping up even in my virtual machine (qemu) but i have no way to verify this. 

Any ideas? Is there any information i can post that can help in solving this issue?

Thanks.

---

### Post by db9s on 2007-04-26
they definately screwed up some USB things. At the moment I'm getting better reliablity WITHOUT a  usb hub

---

### Post by zykris on 2007-04-28
I hope this gets fixed in the next update though. The logs aren't much help too. I'd switch back 2 PS/2 back but I don't have any lying around and I just invested in this keyboard and mouse.

---

### Post by jonjon09 on 2007-04-29
Same stuff happening to me....hopefully it's my laptop so I still can use my keyboard ans touch pad :) but it's really annoying to have to use the touch pad...hope this gets fixed soon.

---

### Post by mrazster on 2007-04-29
I have a *Microsoft Wireless Natural* and a *Logitech G7* and I used to have the same porblem when I got both of them connected to USB, my keyboard acts wierd and sometimes it just stops working. But this has been going on since "Dapper Drake" for me...
A solution for me is to connect the keyborad to PS2 thru a USB --> PS2 convereter, and mouse in USB....no problems what so ever.

To me there's no noticeable performance decrease with the converter....

---

### Post by dansteingart on 2007-05-02
I'm having the same keying issues, on a whim I detached my SMC wireless device, things seem better for the moment.  I'm running 7.04 on a dell p4 2.8.

---

### Post by jonjon09 on 2007-05-04
Guys, I have found a solution to my problem! It has been working for me for 2 days so it might help you too. I found the answer on launchpad... I'll paste the reply that explains how to fix it:

NoWhereMan  said on 2007-02-10:

acpi=force irqpoll seems to work...
 to add it to all of your kernel entry, open /boot/grub/menu.lst

scroll until you find defoptions=
and append

acpi=force irqpoll

save, quit and the run

sudo update-grub

reboot and enjoy the fix (let's hope it's a final one!)

---------

I hope this works for you like it did for me.

---

### Post by frank35 on 2007-05-04
I have the same problems with Fiesty. My problem is, I have to log in with a password. There is no way I can fix anything as I can't enter the password without my keyboard. Changing from usb to ps2 doesn't work.

---

### Post by zykris on 2007-05-04
Hi jonjon09,
thanks for the tip. I've  tried it but i hav problem booting after that. The problem seems to be with irqpoll option. I keep getting this message in my syslog "serial8250: too much work for irq18". Gotta read up more on that but I hope this trick works for someone else though :)

---

### Post by jonjon09 on 2007-05-04
Hum, I didn't get any error when I did that, sorry zykris... Just to make it clearer for some of you if you don't really get the explanation:
You should replace the line:
# defoptions=quiet splash
by this one:
# defoptions=quiet splash acpi=force irqpoll

PS: This is under these lines:
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5

(the file is /boot/grub/menu.lst)

When that's done, just follow the rest of the instructions (save, quit and then run: sudo update-grub .... then reboot and it should work)
Hoping this will help you...

---

### Post by Eredeath on 2007-05-05
I'm unable to get anything to work in my USB; mouse, jump drive, and external hard drive. Luckily i have a laptop with a touchpad but its a pain. I tried to do what jonjon09 said but came up with "Permission denied" when i put it in my terminal. I am the administrator and have the passwords needed to do administrator tasks, so i don't understand why i got that message. :confused:

---

### Post by IanW on 2007-05-05
Eredeath:- You first need to type this into the terminal window...
```
sudo gedit /boot/grub/menu.lst
```
Then change the file according to JonJon's instructions.

---

### Post by Eredeath on 2007-05-05
Wow, i did what lanW said then what Jonjon09 said and everything works now!!!! Thanks so much!  :guitar: :guitar:

---

### Post by zykris on 2007-05-05
> **jonjon09 said:**
> Hum, I didn't get any error when I did that, sorry zykris... Just to make it clearer for some of you if you don't really get the explanation:
You should replace the line:
# defoptions=quiet splash
by this one:
# defoptions=quiet splash acpi=force irqpoll

PS: This is under these lines:
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5

(the file is /boot/grub/menu.lst)

When that's done, just follow the rest of the instructions (save, quit and then run: sudo update-grub .... then reboot and it should work)
Hoping this will help you...


Hi Jonjon09,
I did do it that particular way. Maybe there is some other conflict with the irq. I'll have to go check it out. Thanks for the tip again :)

---

### Post by Thomas Rasmussen on 2007-05-09
I had the same problem and following this tip made my keyboard+mouse work fine, unfortunately hibernate now stopped working... when hibernating it just switches to a blank screen (with blinking cursor) and nothing happens for a loong time... when I then reboot it (using the reboot button, keyboard doesn't respond) it just boots as normal so it doesn't resume.

---

### Post by mishka on 2007-05-22
Hi everybody

I tried the solution of jonjon09 and it works! (At least for my computer configuration 
(LG LE50 Notebook))

Thank you, JonJon09!  :)

---

### Post by jhohum on 2007-05-29
I have an R52 Lenovo (IMB) Thinkpad and just put on Feisty.
I usually operate an external keyboard and mouse through a USB
hub so I can save one on-board USB port for USB disks.  The 
chassis USB port seemed fine (mouse, disk both recognized and
worked) but the mouse through the USB hub was jumping around and
dropping random mouse-clicks (change of focus, undesired text pasted, etc).

I tried jonjon09's solution of adding these to menu.lst and rerunning update-grub

 acpi=force irqpoll


and as far as I can tell, that has fixed the mouse problem.

(thanks!!)

jhohum

---

### Post by jhohum on 2007-05-31
OOps, well I had to reboot and now I'm back to a jumpy mouse using the hub.
No joy in mudville.


Jhohum

---

### Post by divan on 2007-06-12
Guys, "irqpoll" option slowdown the system! Try to make "hdparm -t /dev/hda" - test of your hdd read speed. I have ~15Mb/s with irqpoll option and ~30Mb/s(!!!) whithout this option. USB mouse and keyboard was not worked on my laptop Acer TravelMate 2403, so one way is to enable irqpoll option and slowdown the system, and other way is:
disable option "Legacy USB" in BIOS, and disable "irqpoll" option in kernel load.
"Legacy USB" - BIOS automatic detect USB devices, in other computers this option may called otherwise. Disable it, and linux detect devices by himself, and all work's fine.
So, I disabled ACPI on my laptop too, because this is very buggy. I add "noapic nolapic" options in "defopts" in /boot/grub/menu.lst

---

### Post by Smashing Pumpkin on 2007-06-13
jonjon09, thanks for the tip about using* acpi=force irqpoll* in grub - I was having the exact same symptoms as others have mentioned, but this seems to have fixed my problem.

Just to offer some help, jonjon09's post says to replace the line with:

#defoptions=quiet splash acpi=force irqpoll

For those who didn't spot it, you should also remove the # at the beginning of the line, as this is used to make comments to the file, so with it included the line will be ignored, but without it, it will be acted upon.

Thanks again, jonjon09 :)

---

### Post by Smashing Pumpkin on 2007-06-14
Actually, I was completely wrong... you do need to keep the # and not do what I said. I found that when I had uncommented it the problem came back when I had to reboot, and the changes I had made were no longer there. But then when I was adding the change again I saw a comment in the file that says to not uncomment the file, so I tried that and it's now working great even after reboots.

So, ignore my previous post as I was completely wrong.... and kudos again to jonjon09 for resolving my USB problems :)

---

### Post by yes9111 on 2007-07-12
ZOMG
EXACT SAME PROBLEM THAT I HAVE.

At some point,
it starts going TTTTTTTTTTTTTTTT or DDDDDDDDDDDDDDDDDDDDDD
and mouse freezes too...
Must be my 10th or 12th time restarting my computer today...

Hope this gets fixed really fast =)

EDIT - 
Saw the fix.
Cried in happiness.
Edited the file.
Am seeing if i can survive 15 minutes of free motion...

---

### Post by ginyip on 2007-09-05
No solution works so far. I have tried both the Legacy USB off option and irqpoll option. They don't work for my machine.

noapic option might seem to work but kernel only figure out 1 core on a 64 bit CPU.

I am trying to dig more. google, I am coming.

---

### Post by Onythias on 2007-09-19
I'm having the same problems, with no solution so far.  Neither changing the menu.lst file or the USB legacy option fixed it (changing usb made it worse actually).  Fortunately I have a PS2 mouse and keyboard handy.

---

### Post by Phatalic on 2007-09-23
I have the exact problem, im running Ubuntu Ultimate Edition 1.4, with Fiesty. I own a wireless keyboard and mouse setup that uses the serial ports and recently a friend gave me an apple usb keyboard. So i took the batteries out of the keyboard kept the wireless mouse in and used the mac keyboard. It worked fine with windows, but now has issues with fiesty. Ill login and everything will be fine i could use both keyboards but everytime id run packet manager for anything (new vid card driver, ultimate upgrade) my mac keyboard would die but i can still use the serial wireless one. I can sit here and press the caps lock on my wireless keyboard and watch the caps lock light on my mac keyboard turn on, but when i press it nothing happens. 


looks like im back to the old wireless keyboard for now

---

### Post by derek45 on 2007-12-03
I just tried the irqpoll and, so far, so good.....

......fingers crossed.:)

---

### Post by derek45 on 2007-12-03
USB mouse just locked up.

since the "irqpoll"  mod did not fix it,  should I remove it,  or leave it in there?

---

### Post by sendtoscott on 2008-07-04
> **jonjon09 said:**
> 
acpi=force irqpoll seems to work...
 to add it to all of your kernel entry, open /boot/grub/menu.lst

scroll until you find defoptions=
and append

acpi=force irqpoll

save, quit and the run

sudo update-grub



That just made my mouse screen pointer disappear completely.  This is why I try but give up on Linux annually - there are always one or two deal-breaker problems where the answer is "Edit this system file, or that system file, or this other system file.  One of those may fix the problem or make it worse and you have to figure it out."

---

