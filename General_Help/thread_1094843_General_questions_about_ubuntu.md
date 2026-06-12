---
title: "General questions about ubuntu"
date: 2009-03-13
forum: General Help
---

### Post by Bridge Hanson on 2009-03-13
Hey, I recently received my ubuntu 8.10 disc in the mail, and after trying the test thing where you keep the disc in the drive and restart the computer.... well... I wasn't too impressed.

The system took a long time to load, and when it did, it was pretty slow. One time it seemed to freeze, but after about five minutes everything seemed to go fine again. However, throughout the whole thing, many options would bring up an error message (network connections and computer come to mind) and would not load.

My first impression, and question, is this: is this because I'm testing from the disc instead of installing it? I thought maybe it doesn't work fully unless you actually install the program.

If so, then I have some other questions as well.

If it was just the disc, then I was thinking of making ubuntu my sole operating system. This desktop is soley for college and working information for me, so I won't be needing things like PC games and such. But I will need a few things, naturally, and in my ignorance of the program (not knowing much about it other than general information), I need to know if these certain things will work. I apologize if these are obvious yes' or no's in advance:

Will my USB ports work so I may use my flash drive?
Will my printer (Lexmark X1240) work if I install it?
Will my wireless card (built into the computer) still be able to connect to wireless connections?

This one isn't a requirement, but will be very helpful:

Would I be able to install MSN Messenger? It's a main means of contact to my fiance as I'm busy with college. However, we can always switch to a program that will work for both our OS's.


I don't really want to keep to OS's on one computer, since it'd be quite a hassle to have to switch between both systems, but those three main questions are definite requirements (naturally) for my computer. They may be obvious, but I'm dead new to all of this.

And is the OS itself faster than the disc test? Because it took a slow load to start up and it was pretty skippy/laggy afterwards. I was contributing it to the fact I was working an OS from a CD, so I want to be sure ahead of time.

Last question: if I do install it while also keeping Windows XP as an operating system, can I later remove XP without losing any new files on Ubuntu?


Thanks for any help! Sorry if I've posted this in the wrong area.

---

### Post by cariboo on 2009-03-13
What are the specs of your computer, do you have a minimum of 512Mb of ram, if not the LiveCD will run slow.

> Will my USB ports work so I may use my flash drive?
Will my printer (Lexmark X1240) work if I install it?
Will my wireless card (built into the computer) still be able to connect to wireless connections?

Your usb ports will work and usually flash drives are auto-mounted,

Your printer will partially work see the [OpenPrinting database]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-X1240"). Lexamrk North America does not do a very good job of creating Linux drivers for their printers.

If your wireless card works with the LiveCD, it will work when you have installed Ubuntu.

Most Windows programs will work if you use Wine, which is a software layer similar to Windows.

I would suggest dual booting until you have everything working, as sometimes thing don't work as expected.

Jim

---

### Post by Bridge Hanson on 2009-03-13
I meet the requirements, I believe. My RAM might be exactly at 512, and my processor is 2G.

I couldn't test the wireless in the test on the disc, since the error message kept appearing. But the message came up with other things too, so I figured it was something with the test, and not the wireless.

---

### Post by lindsay7 on 2009-03-13
I am a new user of Ubuntu also, but I have put it on four computers in the last month.  I tell you what I know with respect to you questions.

USB normally work with nothing needed.
From what I know most printers work and are plug and play but I have seen some post talking about some that do not.
Wireless cards a touchy some work plug and play others neeed some work.
MSN and the others like work (as far as I know)and there are options in Ubuntu if they do not.

My suggestion would be to install Ubuntu Under windows. You should be able to do it with the disk you downloaded.  If so, put it in the computer and open it under windows. You will see that option if you disk is set up like that. If now go to the “WUBI” web site and it will self install.  This way you can try everything and see how it works or does not work for you.  You will be able to boot to windows or Ubuntu then you turn your computer on.  If you want to get rid of Ubuntu, you can uninstall from the control panel in windows. There is a way to get rid or Windows under this set up but it is a little complicated.

I did the install under Windows and like Ubuntu so much that I went to a full dual boot system after less that a week later.

---

### Post by iaculallad on 2009-03-13
> **Bridge Hanson said:**
> Hey, I recently received my ubuntu 8.10 disc in the mail, and after trying the test thing where you keep the disc in the drive and restart the computer.... well... I wasn't too impressed.

Why? Did it boot from the LiveCD?

> **Bridge Hanson said:**
> The system took a long time to load, and when it did, it was pretty slow. One time it seemed to freeze, but after about five minutes everything seemed to go fine again. However, throughout the whole thing, many options would bring up an error message (network connections and computer come to mind) and would not load.

What are the specifications of your PC?


> **Bridge Hanson said:**
> My first impression, and question, is this: is this because I'm testing from the disc instead of installing it? I thought maybe it doesn't work fully unless you actually install the program.

Actually, the LiveCD is just a replica of when you install it on hard drives.



> **Bridge Hanson said:**
> If so, then I have some other questions as well.

If it was just the disc, then I was thinking of making ubuntu my sole operating system. This desktop is soley for college and working information for me, so I won't be needing things like PC games and such. But I will need a few things, naturally, and in my ignorance of the program (not knowing much about it other than general information), I need to know if these certain things will work. I apologize if these are obvious yes' or no's in advance:

> **Bridge Hanson said:**
> Will my USB ports work so I may use my flash drive?

Absolutely.

> **Bridge Hanson said:**
> Will my printer (Lexmark X1240) work if I install it?

I'm not just sure about the printer issue.


> **Bridge Hanson said:**
> Will my wireless card (built into the computer) still be able to connect to wireless connections?

Depends on the hardware model.

> **Bridge Hanson said:**
> This one isn't a requirement, but will be very helpful:

Would I be able to install MSN Messenger? It's a main means of contact to my fiance as I'm busy with college. However, we can always switch to a program that will work for both our OS's.

MSN protocol is supported by Pidgin.


> **Bridge Hanson said:**
> I don't really want to keep to OS's on one computer, since it'd be quite a hassle to have to switch between both systems, but those three main questions are definite requirements (naturally) for my computer. They may be obvious, but I'm dead new to all of this.

And is the OS itself faster than the disc test? Because it took a slow load to start up and it was pretty skippy/laggy afterwards. I was contributing it to the fact I was working an OS from a CD, so I want to be sure ahead of time.

Yes, hard drive installed runs much faster than running on LiveCD's.

> **Bridge Hanson said:**
> Last question: if I do install it while also keeping Windows XP as an operating system, can I later remove XP without losing any new files on Ubuntu?


Thanks for any help! Sorry if I've posted this in the wrong area.

Yes, if both OS are loaded under GRUB.

HTH.

---

### Post by Bridge Hanson on 2009-03-13
alright, thanks. Sounds like my best bet would be installing it dual and seeing how it goes. Does anyone know why the error messages appeared? Was that just demo error?

---

### Post by iaculallad on 2009-03-13
> **Bridge Hanson said:**
> alright, thanks. Sounds like my best bet would be installing it dual and seeing how it goes. Does anyone know why the error messages appeared? Was that just demo error?

It would be better if you try posting the error message so we could help you decode it :D

---

