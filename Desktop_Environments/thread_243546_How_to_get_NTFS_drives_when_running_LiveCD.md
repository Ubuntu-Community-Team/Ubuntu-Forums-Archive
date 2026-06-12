---
title: "How to get NTFS drives when running LiveCD?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Endersothergame on 2006-08-25
OK, here I am looking at this great and wonderful new thing (not sarcasm, it is nice looking)  However it is a quiet room here as all my music appears to be locked away on my storage disk, formatted NTFS naturally and it seems that I can't have the data.  I am not prepaired to install this OS yet until I am sure I like it, but i really want to fool about for a while with some tunes.  Can anyone help me?

I say this closely followed by asking, how do I get MP3 support as well.

---

### Post by gibbylinks on 2006-08-25
Make sure you have eveything backed up and then install Ubuntu as a  dual boot system. That's what I've done.
This enables you to try things out and play with Ubuntu, learning and gaining confidence. You can now set it up to write to NTFS drives as well as read from them so you can get to your music.
It doesn't matter wether I'm in windows or Ubuntu for my Firefox bookmarks and my E-Mails as they are shared between the OS's.

You can also run Compiz & XGL which are amazing eye-candy and blows windows away.

The only reason I still have my windows partition is I begrudge deleting the OS and some of the software when I've paid for them. If all of my software was pirated or came pre-installed it would have been zapped long ago.

Go On take the plunge and install.....

---

### Post by Endersothergame on 2006-08-25
So thats it?  no NTFS support w/Live CD? 

Hmm I wasn't wanting to move this fast but without anothr option its feeling all or nothing.

---

### Post by gibbylinks on 2006-08-25
Sorry in my haste to publicize Ubuntu, I forgot to answer your question.
If you goto system, administration, disks and find the details for your NTFS partition you should then be able to mount it manually 

1. Make mount point.

2. Mount music partition.

In a terminal enter the following set of commands:
Code:

sudo mkdir /media/music
sudo mount -t ntfs /dev/**** /media/music

replace **** by the partition name, i.e hda1

---

### Post by Endersothergame on 2006-08-25
excellent I shall give it a try and let you know how it goes

---

### Post by tuxcantfly on 2006-08-25
you can also use this guide to set up read-write access:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

just note that you'll have to do it over again every time you reboot. that's why you should install to hd. but it'll work just fine in the live cd, in case you need to do system recovery or something (the one gibbylinks described was for read only. this is read-write)

---

### Post by peabody on 2006-08-25
I was considering recommending Ubuntu to my friend for LiveCD stuff, but realizing that you need to resort to the command line for that gives me second thoughts.  Does anyone remember if Knoppix sets up icons automagically for mounting ntfs partitions?

Edit:

> 
you can also use this guide to set up read-write access:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)


On a Live CD??  Highly not recommended.  Sometimes partitions don't get properly unmounted especially if you just power off :-s.

---

### Post by tuxcantfly on 2006-08-26
>   I was considering recommending Ubuntu to my friend for LiveCD stuff, but realizing that you need to resort to the command line for that gives me second thoughts. Does anyone remember if Knoppix sets up icons automagically for mounting ntfs partitions?
 
 Edit:
 
 
Quote:
 you can also use this guide to set up read-write access:
 
 [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
 

 On a Live CD?? Highly not recommended. Sometimes partitions don't get properly unmounted especially if you just power off .

yes, knoppix provides automatic read-only mounting, at least for the last one I tried (3.8). as for the unmounting issue, you can solve it all with a sudo umount /media/ntfs (or whatever your mountpoint is), so that the partition gets properly unmounted. besides, a lot of people use ubuntu or other linux live cds for recovering their windows installations, so read-write ntfs support on live cds is crucial.

---

### Post by peabody on 2006-08-26
[http://www.newhorizonssucks.net/LiveCD.html](http://www.newhorizonssucks.net/LiveCD.html)

The guys an *** about it and really harsh, but it's something to think about when Knoppix puts icons that you can just click mount.

---

