---
title: "AIO Printer [dell] won't work - how do i share with my M$ OS"
date: 2008-05-01
forum: Desktop Environments
---

### Post by Vesper007 on 2008-05-01
Hello
I cannot get my dell printer to work under Linux ...so how can i get files i want to print onto my Windoze OS from linux 7.10?
 
[dell printer works on M$ system]

---

### Post by loserboy on 2008-05-01
which AIO is it, look it up here [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting) there should be some helpful info on it

---

### Post by Vesper007 on 2008-05-01
AIO 926....have done lots of reading on searches for this type on this Forum...it seems that 925 does not have a fix for linux...thanks for the link to 'open printing'  - I've scanned the site and will look at it closer later.  
 
I have a 1GB (yes...that's a ONE) hd that is not being used. Can i use it to store Linux and M$ files and can a windoze document be opened in Linux and can Linux document/files be opened in M$
 
How do i mount my floppy 3.5 ????  
(this is probably the wrong place for this question....but i was on a roll and had to ask it)

---

### Post by loserboy on 2008-05-01
np the linuxprinting site is awesome, anyway yes u can use the 1 gig hd (lol) for storage by simply formatting as FAT32. unless u need it with a different file system that's the easiest way.

um, I haven't used a floppy in a while, but it should be the same as any removeable media and just automount when u stick in a floppy, if it doesn't then you can go to Places>Computer>Floppy drive

hope this helps


edit: oh i forgot to answer your other question. it all depends on the type of document you are trying to open, if you are talking about text or spreadsheet type files then openoffice (ubuntu's default word processor) can open most of the different filetypes. out of curiousity what files do you mean?

---

### Post by Vesper007 on 2008-05-01
:) Put floppy into drive [3.5] and double clicked floppy on "Places" menu. [INDENT][INDENT][INDENT]Error:  Unable to mount floppy.
[/INDENT][/INDENT][/INDENT]Floppies are archaic, but i developed a habit of using them to store my journals.

Is there a boot sequence that can be done that will allow me to switch from Linux to M$....on the fly [from a game in M$ to a doc in Linux - things like this...quick switches on the go as needed

I see that my 1GB drive is NOT listed in "Places" or under "computer" in Linux OS... 

is there a way to look for it and "tell" Linux that it's there, and then format it in FAT32?

Decided to use  USB Flash/thumb drive for journals but would still want to know how to mount a floppy under Ubuntu.


Thanks again to all who feel they can help me out. 
cheers, eh

      V7

---

### Post by loserboy on 2008-05-02
[http://ubuntuforums.org/showthread.php?t=106544&highlight=pmount+update+floppy](http://ubuntuforums.org/showthread.php?t=106544&highlight=pmount+update+floppy) old thread about mounting floppy, dunno if it's still useful, but just try googling "mount floppy in ubuntu"

i can't think of any way to switch from one actually booted from another, but depending on the windows game you may be able to run it from WINE ( winehq.com) inside ubuntu.

you prolly can't see the hd because it doesn't have a mount point, prolly the best thing to do is boot with the ubuntu livecd and run 
> sudo GParted
then you can see the hd and format it and set the mount point as /media/backup or something, careful with gparted though u can wipe everything.

before you do anything read this site [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) it should have info about mount points and such

sry im not at a linux computer right now so this is all off the top of my head

---

### Post by Vesper007 on 2008-05-03
Hey, hey, hey;

It's a great day indeed. My floppy is working. I didn't do anything except accidentally left 3.5 journal disk in the drive. On next boot, it was interrupted (which means it actually called up the floppy and recognized it was not a systems disk) was this a fluke or is great programming on the development side of thing. I like to think the latter; duh!

I'm saving my 'shared' files via the 1gb disk....also on the next boot sequence, my computer recognized my windows disk and my storage disk... 

all is well with this concern now. 
thank you all for contributing to the fix. (all successes are a result of standing on the shoulders of those who have traveled the path ahead of us 


V7

---

### Post by silbar on 2008-05-03
> **Vesper007 said:**
> Hello
I cannot get my dell printer to work under Linux ...so how can i get files i want to print onto my Windoze OS from linux 7.10?
 
[dell printer works on M$ system]

I have exactly the same problem.  Going to the OpenPrinting database suggested by LoserBoy (why did you pick THAT name?), it appears that the Photo AIO 926 printer is designated as a "paperweight".  Does this mean that a driver has not yet been written for it?

  Dick Silbar

---

### Post by loserboy on 2008-05-06
> **silbar said:**
> I have exactly the same problem.  Going to the OpenPrinting database suggested by LoserBoy (why did you pick THAT name?), it appears that the Photo AIO 926 printer is designated as a "paperweight".  Does this mean that a driver has not yet been written for it?

  Dick Silbar

heh, ive had the same name for at least 10 years, anyway it's not a good sign if it says paperweight, sry.

this is what someone said why it doesn't work 

> due to the low cost features of the printer that use only a proprietary driver data stream. 



---

### Post by avtolle on 2008-05-06
I used this to be able to print from Vista on a Brother MC240C for which there were no drivers for PPC Linux; it worked. HTH. Subsequently have put Hardy on the Vista machine, and have no issues printing among my boxes. Also used this, plus another tutorial (which I don't have right now) to allow printing from Vista on a printer attached to one of my Linux boxes. 
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

