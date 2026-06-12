---
title: "Alien - Ubuntu Breezy"
date: 2005-10-17
forum: Desktop Environments
---

### Post by lonetree on 2005-10-17
Just got Breezy up on my notebook, as a testbed before I upgrade all my other desktop to Breezy from Hoary.

Its a shock to me. Instead of it getting better, I felt that Breezy is far from better than Hoary, my opinion anyway.

I notice that the alien command is not available bt default, I got a shock initially, thought I issued the wrong command. Then I went into synaptic to install alien.

Another thing I notice is the network speed is much more slower than what is used to be in Hoary, already Hoary is slow in the network speed, I can hardly get a bandwidth of more than 1000kb and now in Breezy, its even worse.

What happened?

Regards,

---

### Post by rmjokers on 2005-10-17
Perhaps the network you are connecting to is conjested at the moment?  You cannot expect to get the same throughput all the time unless you are using your own private network.  Could you be more specific?

For point number two, if Ubuntu included every application that anyone liked, it would take 2 DVD's to install like Debian.  You should be thankful that alien is in the repository and is easy to install.  They cannot include everything in the single CD base install.  For every cool feature that they add, they have to remove something obscure and less popular.

---

### Post by Pablo_Escobar on 2005-10-17
alien not in the default install - and I think it's a well thought idea.
alien changes rpms to debs, and we all know that only a small % can be installed well this way.
And it's better for new users not to fiddle with alien and make a useless garbage out of their system.

thats my 2p.

---

### Post by lonetree on 2005-10-17
[QUOTE=rmjokers]Perhaps the network you are connecting to is conjested at the moment?  You cannot expect to get the same throughput all the time unless you are using your own private network.  Could you be more specific?

For point number two, if Ubuntu included every application that anyone liked, it would take 2 DVD's to install like Debian.  You should be thankful that alien is in the repository and is easy to install.  They cannot include everything in the single CD base install.  For every cool feature that they add, they have to remove something obscure and less popular.[/QUOTE]

of course I wouldn't be so stupid to comment on internet bandwidth. I am talking about my internal LAN network speed, and I have actually tested and compared. I think there are a few guys in here have this problem too.

If you don't believe, test it out with a windows system and compare.

---

### Post by joelito on 2005-10-17
Do you happen to know if your router supports ipv6??

Because I noticed people having trouble with it

---

### Post by rmjokers on 2005-10-17
What type of information transfer are you using to determine the throughput?  Is it an FTP, SFTP, or HTTP transfer?  Is it SMB or NFS traffic?  How big are the files?  Is this a 10 Mbps or 100 Mbps ethernet connection?  Is it a wireleses connection?

---

### Post by lonetree on 2005-10-18
1. No. As far as I know, my router does not support ipv6. I'm using a Dlink DI-724P+ and in office, I'm using a DI-624+. What's next?

2. I'm transfering my files using smb, and at home I have a NAS, a simple one from vgear, and it has ftp function, all these transfers are too slow compare to using windows. In these 2 environment, I'm using 100 base.

What's next?

thanks

---

### Post by rmjokers on 2005-10-18
There are a few things you might try.  First, look at the file:

/var/log/messages

and make sure that the kernel is actually setting up your ethernet interface to use 100Mbps full duplex.  My kernel prints this:

Link is up at 100 Mbps

Also, you could run some tests on your hard drive to make sure that DMA is enabled.  Try running:

hdparm /dev/hda

and

hdparm -tT /dev/hda

to get information about the current configuration and to get timing measurements on the first IDE drive.  I get values in this range:

 Timing cached reads:   3588 MB in  2.00 seconds = 1794.27 MB/sec
 Timing buffered disk reads:  166 MB in  3.04 seconds =  54.69 MB/sec

If you get numbers significantly lower than this (< 5 MB/sec for buffered disk reads), then DMA may not be enabled for your drive, which could cause a significant slow down in network transfers.  You can enable DMA and other features by editing the /etc/hdparm.conf file.

Nothing else comes to mind at the moment.  Good Luck!

---

