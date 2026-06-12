---
title: "Desktop contents suddenly nulled"
date: 2009-08-05
forum: Desktop Environments
---

### Post by leiurus on 2009-08-05
Hi,

I have a problem finding my desktop stuff...

Have been using 804 for some time and just recently got this problem that doesn't seem to be related to other discussions regarding accidently deleted desktop items etc.

Quick explanation:
I was doing nothing in particular. And I was NOT deleting anything, neither the desktop folder itself nor anything in it. Used my Sandisk 8GB SDHC card a little and mounted/umounted a few times - this has always worked without problems.

I also used the Kismet app just before the problem started and I also mounted a M$ share and copied a few files - this too has also worked without problems earlier.

Then what happened was that when I was trying to open a folder on the desktop, just double clicking on it - at this time the desktop showed all items as usual - I got an error stating something about folder not existing. I got surprised and tried to open another one and got same error.

I then rebooted, thinking that there was some random error or something out of sync. But now after rebooting the desktop was empty, completely empty instead.

Checking with ls -l in shell also yields 0 files in Desktop folder (and Desktop folder exists).

Disk is not full. System did not crash (although Kismet often does upon exiting). Did no editing of config files or similar.

That's about it - can anyone comment on what may have happened?!


TIA,

---

### Post by realzippy on 2009-08-05
..used other aircrackstuff?
...shure not to be in /root/Desktop ?

---

### Post by leiurus on 2009-08-06
> **realzippy said:**
> ..used other aircrackstuff?
...shure not to be in /root/Desktop ?

No, only use Kismet as a Netstumbler like app to check signal levels on my APs. I have tried other similar apps but they all crash more or less.

And doing Netstumbler under WINE seemed to work but it couldn't find any network adapters..

Doing sudo su and being root and checking around I find nothing. I don't even have /root/Desktop...

I think this feels like file system messed up or perhaps faulty drive or something.

This is an eeepc900, no regular HD, BTW. (And it has only been used for some 6-8 months so drive shouldn't be worn out either?)

I have seen other threads on subject dissapearing desktop items but then people have most often accidently deleted things. I have my /home/user/Desktop folder intact BUT when checking even in shell it is holding "total 0"!

It looks like the items have been removed. 

Also note my description on how the problem appeared first time, I was in my desktop and items were showing on screen.

Unfortunately this makes me somewhat suspicious, I don't know if Ubuntu did this or if something else is to blame. I may have lost a few things too, but not too much I think, I have an Acronis image of the disk that is >95% accurate, minus a large system update, but that I can always run again.

I also checked in some file /home/user/.config/user-dirs.dirs but that seems 100% correct.

Is there some "undelete/data recovery" app for Ubuntu I could try, like Ontrack's software or something, if the file system messed up the data, it is still there somehow, if the flash disk's properties don't make this different somehow.

But I should probably boot an external OS to do such a thing anyway I guess.

I need more help pls...

TIA,

---

### Post by leiurus on 2009-08-11
Ok, since noone have given me any additional suggestions I'll reinstall.

However, I did notice that the system sort of "hangs" at the Desktop folder when browsing the folder using the GUI, when pressing 'Desktop' folder it stops, saying "loading" and nothing happens.

This seem to suggest that there's some file system corruption or somethin involved, it does not directly report back the folder as empty as it does other empty folders..

That's about it. I'm interested in any suggestions later readers of this thread may have so please post any comments here.

TIA,

---

