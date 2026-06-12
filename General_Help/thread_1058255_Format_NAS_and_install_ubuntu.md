---
title: "Format NAS and install ubuntu?"
date: 2009-02-02
forum: General Help
---

### Post by srnicol on 2009-02-02
I have a NAS server but it doesn't work well and I would like to turn it into an external harddrive. The built in software will only allow connections through a router or wireless router. It has a USB slot and an Ethernet connection. I was hoping I could somehow format the harddrive and install ubuntu and connect it directly to my computer with a network cable, possibly as a home network connection, but preferably as another harddrive.

It's a LaCie 500 gb NAS. Any ideas?

Thanks

---

### Post by lavinog on 2009-02-08
Can't it be used as a USB external drive?
Formating the hd will not remove the current os...most NAS server OSes are firmware.

---

### Post by niteshifter on 2009-02-08
Hi,

LaCie's are strange boxes. As far as getting Ubuntu on it: no. Not enough memory. LaCie does provide the source for the Linux that's already there, but it's not very well documented. You can hack the thing and put a minimal chrooted Debian setup there, this [web page]("http://luon.net/~admar/journal/LaCieEthernetDiskMini.html") is worth a read.

Yeah, I have a LaCie 250GB NAS, thought about doing the above (wanted it be an rsync server). Looked to be a lot of effort for little gain. Pulled the HD out of it and hooked it up via a USB adapter: that's one really odd setup they have there ... and put it back together. It's now my audio jukebox server.

@lavinog: The clever folks at LaCie kill off the USB functionality for Linux. To get the thing to work as a USB drive in Windows requires loading their driver software. As a USB drive in Linux you'll see a tiny partition that has the windows executable for that driver .... grrr.

---

