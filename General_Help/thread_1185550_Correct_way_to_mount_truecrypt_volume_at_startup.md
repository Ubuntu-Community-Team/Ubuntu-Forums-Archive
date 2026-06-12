---
title: "Correct way to mount truecrypt volume at startup"
date: 2009-06-12
forum: General Help
---

### Post by aroundhere on 2009-06-12
Good day,

Using 9.04 ubuntu, and I used the alt installation making my hard drive encrypted on start up.  My box has 2 physical hard drives, both of the same size.  Hard drive 1 was encrypted at installation.  My second drive is empty.  

I followed directions found on the ubuntu wiki and in this forum for setting up the other volume as a Truecrypt drive.   I can now mount it correctly by running TrueCrypt or by typing:

sudo truecrypt --filesystem=ext3 /dev/sdb /extra

All is good.

I'd like for this to mount at bootup.  What would be the best (or most optimal) way to do this?  I assume it would prompt me like my other drive does during boot up.

Thanks for any input or suggestions.  And my apologies if I've missed the answer during my googling and searching of the forum.

---

### Post by statistic on 2009-06-12
My understanding is your trying to mount ANOTHER truecrypt drive during boot, not the decrypt the booting system.

I'm not sure if this is the "correct" way, but the way I do it, which I think is very nice is too add just after the comments section written by "George" in /etc/gdm/Init/Default add your truecrypt line there as though you were doing it manually.

You'll be prompted for the password just before the login screen comes up.

EDIT:
Just to clarify, I suggest you make the file look like:
---------
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George


truecrypt --filesystem=ext3 /dev/sdb /extra
-
-
----------

No need for sudo, as it will be run by root.

---

### Post by michaelzap on 2009-06-12
I'm about to do exactly the same thing, so I'm really glad I noticed this thread. I have one LVM-encrypted SATA drive (running Jaunty 64-bit) and another (currently disconnected) almost identical drive that I'd like to mount as an encrypted volume (for secure local backups of a couple of NAS units). I was thinking of doing this with Truecrypt, although another luks volume would work also.

Can you please post a link to how you set up your Truecrypt volume, and if anyone else has alternative suggestions could you please post those?

Thanks in advance.

---

### Post by statistic on 2009-06-12
> **michaelzap said:**
> I'm about to do exactly the same thing, so I'm really glad I noticed this thread. I have one LVM-encrypted SATA drive (running Jaunty 64-bit) and another (currently disconnected) almost identical drive that I'd like to mount as an encrypted volume (for secure local backups of a couple of NAS units). I was thinking of doing this with Truecrypt, although another luks volume would work also.

Can you please post a link to how you set up your Truecrypt volume, and if anyone else has alternative suggestions could you please post those?

Thanks in advance.

I'm confused as to what information you're looking for here Michael.

If you need installation help, just go to [www.truecrypt.org](www.truecrypt.org) and download the installer, then run it as root. and follow the steps. Once you've done that, just run the truecrypt gui and it's all point and click delight from there. 

To mount it just before logging in, use the idea I gave in my previous post. However if your main drive is truecrypted as well, it might not be a security issue to hardcode the password into a startup script somewhere. Just be careful if you do that, and don't forget the password.

---

### Post by michaelzap on 2009-06-12
aroundhere had just said:> **aroundhere said:**
> I followed directions found on the ubuntu wiki and in this forum for setting up the other volume as a Truecrypt drive
so I thought perhaps there was a particularly helpful forum post that I might want to look over before blundering into setup on my own.

I also wonder if I need to mix encryption systems, however, since I'm already using regular LVM encryption for my main system drive. Is there any negative to just doing this for the backup drive as well? For example, if later I wipe my system drive and install Koala, will I be glad that my backup drive is Truecrypt-encrypted instead of LVM, or is it about as easy to deal with either way? And if I had to pull the backup drive out of my system and recover the data somewhere else, would TC make that significantly easier? I'm not really desperate for answers, just wondering if folks reading this have insight they'd like to share.

---

### Post by statistic on 2009-06-12
Sorry, I don't think I know enough about LVM to help you there, but the use of truecrypt would be completely portable from system to system, and from OS to OS.

If anyone has more knowledge about LVM that would likely give Michael more useful information.

---

### Post by aroundhere on 2009-06-12
Thanks for the input so far, I'm going to do whats recommended up above and let you all know how it goes.

For those inquiring how I set up truecrypt; I followed the following directions:
[https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

But I had lots of problems installing TrueCrypt itself at first, what I did was after I got the deb file I had to use dpkg to install it, for some reason ubuntu was unpleasant with the truecrypt installation from truecrypt.

Hopefully that will help someone,

-aroundhere.

---

### Post by Soul-Sing on 2009-06-12
installing truecrypt:
sudo sh path/to/the download/truecrypt-<version>-setup-ubuntu-<"architekture">

---

### Post by aroundhere on 2009-06-19
Well, I finally got a chance to reboot, and got prompted for my truecrypt password.  My disk mounted.  And I thought, yay!

But alas, its empty.  The gigs of data I had put on it previously were all gone.


Any thoughts on this?  It reads as an empty drive.  I can write to it again.. but the data that was there is like it never existed.

---

### Post by aroundhere on 2009-06-19
Ignore the above.  I made a very simple mistake.  Had drive unmounted and wrote to the directory.. sigh.............  

Thanks for all the info above.

*head hung in shame*

---

