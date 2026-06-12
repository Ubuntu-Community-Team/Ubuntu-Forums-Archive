---
title: "Installing Ubuntu server on an IDE Flash Drive - Help and tips required!"
date: 2008-12-31
forum: General Help
---

### Post by the.ciscokid on 2008-12-31
Hi all, 

I have been doing alot of forum surfing, so apologise if I have missed something fairly obvious.  I have just built a new server, and was hoping to add a 2Gb IDE flash disk to it.  My thinking is that it will reduce noise and power consumption, since I am planning to keep it always on (but maybe with some kind of standby/ wake on LAN type set up... but i'll work on that later.

I had better mention I am pretty much a Linux noob - though I have a rough idea of the command line as I use Unix a little at work.

To the immediate issues - 

I am planning to USB install onto a 2Gb IDE flash disk following the instructions [https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller]("here")

Anyone see any initial problems with that?  I may (though may not...) want to aptitude intall a gui at some point if I get totally lost...

IDE flash I am aware wont last forever, so I was hoping to get some advice as to how to increase the life expectancy so to speak.  

The box I am using has 2 gigs of RAM, and I was hoping that this would mean I don't have a need for a swap partition.  Is that correct, and if so, is that something I simply don't configure - so to speak - during the installation?

Ext2 apparently doesn't use a journal (whatever that is) meaning less excessive writes to the flash drive.  This can only be a good thing?

I have been reading a bit about mounting the /var part of the filesystem on a different partition - again is this something I can configure at the installation, and will I need to do something post installation?

Finally - making the filesystem read-only... the idea of this server (apart from a learning experience with Linux) is as a data server (samba shares etc) with the potential to make it a webserver etc. later.  I want to ensure that the 1TB hard disk is read writable (obviously), so is it feasible to had the file OS filesystem read-only?  If this is so, anyone care to give me a few pointers?

Thanks in advance everyone... sorry about the ridiculously long post.

---

### Post by albinootje on 2008-12-31
> **the.ciscokid said:**
>  The box I am using has 2 gigs of RAM, and I was hoping that this would mean I don't have a need for a swap partition.  Is that correct, and if so, is that something I simply don't configure - so to speak - during the installation?

You can skip the creation of a swap partition during the installation.
> 
Ext2 apparently doesn't use a journal (whatever that is) meaning less excessive writes to the flash drive.  This can only be a good thing?

Yes.
> 
I have been reading a bit about mounting the /var part of the filesystem on a different partition - again is this something I can configure at the installation, and will I need to do something post installation?

Can indeed be done during the installation.
> 
Finally - making the filesystem read-only... the idea of this server (apart from a learning experience with Linux) is as a data server (samba shares etc) with the potential to make it a webserver etc. later.  I want to ensure that the 1TB hard disk is read writable (obviously), so is it feasible to had the file OS filesystem read-only?  If this is so, anyone care to give me a few pointers?

Making the filesystem read-only can be a hassle to maintain.
A firewall project like m0n0wall gives you the option to boot from cdrom, and put your configuration on a floppy.
You can make the floppy read-only when you've got your configuration right, but in your setup things are much more complicated imho.

Just make sure to read about certain mount options for different partitions (like noexec,nosuid,nodev), read about security for webservers, make regular backups, do regular file integrity checks.

GL!

---

### Post by the.ciscokid on 2008-12-31
> **albinootje said:**
> Making the filesystem read-only can be a hassle to maintain.
A firewall project like m0n0wall gives you the option to boot from cdrom, and put your configuration on a floppy.
You can make the floppy read-only when you've got your configuration right, but in your setup things are much more complicated imho.

Just make sure to read about certain mount options for different partitions (like noexec,nosuid,nodev), read about security for webservers, make regular backups, do regular file integrity checks.

GL!

Hi albinootje, thanks for replying.  I guess the plan is that I won't really (intentionally) be modifying the file system once I have it set up as a file server (but plan to do a bit of fiddling and reading on what I can do next)...  But during the normal operation of the system, I want to try to avoid unnecessary writing to the flash disk... which is where the read-only file system came into it.  

On the other hand, for the sake of a £20 IDE flash disk I don't want to make my life more difficult - so I take onboard what you say about it being a hassle.

How often are the volatile ares of the file system accessed would you imagine during normal operation?

Can I also ask, with regards to noexec, nosuid, nodev - are you meaning the same idea as /var - and mounting these on the hard disk?

Thanks!

---

### Post by albinootje on 2008-12-31
Okay, hmm, sorry, I assumed right away that you wanted a read-only filesystem for security sake.
Here's an example about reducing writing to the flash memory, to give you some ideas :
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
The "REDUCING SSD WEAR" section.
After installation it will be /tmp and /var will be written in the most.
You can choose to make those partitions on the real hard disk.
> 
Can I also ask, with regards to noexec, nosuid, nodev - are you meaning the same idea as /var - and mounting these on the hard disk?

I meant that only for security too, for example when having a /home with public_html directories visible via the webserver on the net.
When an attacker manages to break in, it's likely that they want to execute their own scripts. Using certain mountpoint options for /home and /tmp can be handy concerning that.
But again, it's much more important to secure your webserver properly. Badly written php and cgi scripts, and forgotten security updates are the first "open door" to break in from the net.

---

### Post by the.ciscokid on 2008-12-31
> **albinootje said:**
> I meant that only for security too, for example when having a /home with public_html directories visible via the webserver on the net.
When an attacker manages to break in, it's likely that they want to execute their own scripts. Using certain mountpoint options for /home and /tmp can be handy concerning that.
But again, it's much more important to secure your webserver properly. Badly written php and cgi scripts, and forgotten security updates are the first "open door" to break in from the net.

Ok - WOW - that's a little over my head at the moment if I am honest!  Yeah, in terms of web serving, this will only really be for the learning experience... and I wont be looking into that sort of thing straight off the bat.

Thanks for clarifying everything, and thanks for the link.  I'll look through all that tonight!

---

