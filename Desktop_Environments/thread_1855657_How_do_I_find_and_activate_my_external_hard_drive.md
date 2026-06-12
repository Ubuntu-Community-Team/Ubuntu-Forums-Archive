---
title: "How do I find and activate my external hard drive?"
date: 2011-10-06
forum: Desktop Environments
---

### Post by ec1955 on 2011-10-06
I am new to linux, so I don't know the lingo or my way around to find things.
I have a 1tb western digital ext hdd on my computer but it doesn't seem to be working.
where do i find it on linux and how, if needed, do I get it working?

Thanks
Ernest

---

### Post by tgalati4 on 2011-10-06
Plug in the drive, open a terminal and paste the following to this thread:



sudo fdisk -l  *(That's a lower case "l" which stands for list drives.)*

and

dmesg | tail -40

---

### Post by ec1955 on 2011-10-06
Sorry for sounding stupid, but do you mean 'search bar' for terminal?
If so, I open one, pasted code and found nothing.
It found my printer, scanner, and other usb device by itself, but not my hdd.

Can you be a little more more specific for me?
Thanks
Ernest

---

### Post by tgalati4 on 2011-10-06
Right Mouse Click on the desktop background--"Open Terminal"

or Accessories-->Terminal in the menu.

Cut and paste the commands and cut and paste the output into this thread.

Do you not see your hard disk when you open the folder "Computer"?

---

### Post by Rasa1111 on 2011-10-06
I also have a 1TB WD external drive..
and i just plug it in, and the folder opens right up, and shows the drive on my desktop. 
(or in Unity now).

Just like any other thumbdrive or anything else.
Not sure what's up on your end. 
I have a few external drives..
and all work the exact same. Always have.

good luck

---

### Post by ec1955 on 2011-10-11
Well, when I look into FILE SYSTEM -DEVICE -DISK -by -ID I find something there - but I don't know to get it to open - it worked fine on my other computer
Thanks

---

### Post by proxy.qtz on 2011-10-11
make sure it's plugged in and turned on, first. make sure the cable connecting it works, and that you can connect stuff to the port it's connected to. also, you could try looking for it in nautilus.

---

### Post by wkulecz on 2011-10-11
I had a Western Digital external USB hard drive that had a "CDROM" partition with some lame windows and mac software.  It messed up mounting under Linux.  You can download a utility from WD to remove it but its only for windows and you'll lose any data you may have on the drive now.

May or may not be your problem but if a mysterious CD icon appears on your desktop when its plugged in, likely it is your problem.

---

### Post by ec1955 on 2011-10-11
Well, I found something under the place I mentioned above 'dev-ID' or something - and when I click on PROPERTIES it says 'LINK TO DEVICE BLOCKED'!
This is too weird!
I don't know why this thing doesn't just plug in and work as it did on my other computer.
Thanks
Ernest

---

### Post by Rasa1111 on 2011-10-11
Hey Ernest...
I don't know either!

I've been using Ubuntu for about 2 years and have always just been able to plug in my external drives and be done with it. 

 I've never experienced the problem you're having. :( 
(just so you know it's not Ubuntu messing with you)

Sorry mate.

---

### Post by ec1955 on 2011-10-11
Well, I found out that it doesn't work on my xp computer either!
WD support said something that they did not do a particular thing to the 'elements' in the hard drive and when you try to use LINUX it affects it some way - he made a couple of suggestions which I haven't tried yet - I have been spending my WHOLE DAY on this and you know how this stuff TOTALLY consumes your life - there are great and bad things about computers it does cause you disconnect with 'reality' too much.
Anyway, if all else fails, I guess I will have to take the drive out of the case and mount it in my computer to extract my files and hope to then re-format drive.
Thanks everyone!
Ernest

---

