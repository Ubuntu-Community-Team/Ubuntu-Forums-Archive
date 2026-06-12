---
title: "Let's See If This Makes Sense or Reason"
date: 2010-05-18
forum: Desktop Environments
---

### Post by oldefoxx on 2010-05-18
I've posted many times before, sometimes needing help, and sometimes trying to offer help.  Also tried submitting some bug reports, but that did not go
so well.

Game gets really interesting when you mix it up a bit, like in my case, I
have my wife's PC set up for Ubuntu 9.04 (host) + Sun VirtualBox (VM) + Windows 2000 (guest).  Most times it works okay, but when the keyboard and mouse quit responding, she lets me know about it right away.

I am dealing with two specific applications for my wife.  One is IncrediMail XE, the last version that works with Windows 2000, and the other is Embird 800 for her embroidery.  They both give her trouble about every day.

IncrediMail XE will lock up her machine for awhile.  It also draws two wide bars across the top of the window.  The topmost one is red,  The other is black.  It lasts for minutes, though each may widen a bit more during that time, and my wife generally just powers off turns it back on.  I try to wait it out, and did happen to get a brief look behind the IncrediMail XE windows as it closed one time.  It showed the BSOD image, which makes me think it might have been frozen while a memory dump was being taken.  So maybe something in IncrediMail is making a bad call every once in awhile, and Windows 2000 just dies. until a memory dump is made.
Can't fix it, but they say that just knowing helps.  We will see.

Embird has been tougher.  Wife has a Brother Ult 2001 Embroidery Machine, which takes .PES images from either a memory card or floppy disk.  But it must be the A: drive.  Using a USB floppy drive and passing it to client, it shows up as the B: drive.  Don't know why.  Cannot use typical DOS
commands of ASSIGN or SUBST to remap B: as A:, because Windows 2000 was where they decided to drop DOS even further.  Worked okay for a while by just using B:\ as shared folder, then under Windows, mapping the passed reference as drive A:.  This did work.

But it would not last.  Have to redo the whole process every other day or so.  Today, could not get it to work at all.  Problem seemed to be on Ubuntu side.  Ubuntu would, on its own. decide to either treat it as a floppy drive, a USB device, and each time it should mount, it would create a new subfolder under /media.  So the first time, it would make itself /media/disk, then at some point it would decide to mount it as "1.5 MB Media" and this time it would be /media/disk-1,  and then it would become unaccessable again, and this time you would see /media/disk-2, and so on.     

Isn't that wacky?  One time the shortcut under Windows to a:\ became i:\, which worked for the moment, because Windows asks if you want it to try and restore network connections.  Must have modified the shortcut to use the new drive letter that it picked, when the original was still usable and available.  Trouble is, of course, that Embird says it needs A:

Tried to find some way for Windows 2000 to have the ability to remap A; over B:,  Only clue was that the Registry might be involved somehow.  So searched for B:\.  Not found.  Hey, right now it isn't showing up as USB device, just as shared folder.  Killed Windows, dropped the share, added the TEAC drive in as USB for client. and started Windows again.  Guess what?  This time it shows up as A:\ on its own.  Toy with it for awhile,
but seems solid.  This will work if it lasts, but it hasn't lasted before.

Noted something else a bit unexpected.  With the USB floppy passed on to the client by VirtualBox, why is Ubuntu belatedly accessing it as a USB device with the name 1.5 MB Media and showing its contents in a newly opened window.  Why is Ubuntu doing that when it has been passed off to VirtualBox for handling by the client?

And what is this thing about USB devices anyway?  Other devices have names, related to what they are, and they are grouped into /dev.  Where are the USB devices?  All I know is that they are suppose to be under /proc, but you just try to find one there and tell what it is.  Hey, just being able to find one there would be a start.  Once it gets mounted, somehow, then look for a mount point and see if you recognize it.  Maybe you can, but you try to leave as subfolder for it, and chances are that it will just create another one on its own.  This is rather a mess, wouldn't you say?  But I didn't create it.

Now watch Ubuntu supporters put all the blame on the VirtualBox team.  That is one of the reasons I'm out of the trouble reporting game.  It's always the other sides fault, right?

---

