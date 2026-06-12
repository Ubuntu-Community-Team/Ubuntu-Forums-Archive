---
title: "ubuntu cd privacy traces"
date: 2009-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hello2007 on 2009-07-18
if i popped in my ubuntu cd into a friends computer to use his computer through ubuntu through the cd will any information be stored on his computer? or will it be on the cd? or will it be nowhere?

---

### Post by niteshifter on 2009-07-18
Hi,

When you shutdown  - poof, it's all gone. What passes for storage in a Live CD session is RAM.

---

### Post by hello2007 on 2009-07-18
so its all gone once your done using the computer. Its not even on the cd?

---

### Post by niteshifter on 2009-07-19
Hi,

To be clear: If **you wrote** some file on the machine's hard drive it would still be there after the Live CD session ended - but only if you told some program to save there, the system running from a Live CD is not going do it by accident or in the "background". Most folks use a USB flash drive with a Live CD to save their work.

On a machine already running Linux it may have a swap partition, the Live CD will use it, but no files are stored there, only the contents of RAM should it be swapped. Which isn't likely unless you make the machine very busy (run many programs at once). Windows machines don't have this area, it uses a very different means to swap memory to/from disk.

---

### Post by hello2007 on 2009-07-19
thanks i still havent installed ubuntu so i got 1 more question. Can i view my data on my ubuntu account from my vista account? because i noticed i can view my vista side from ubuntu which is cool even though i cant open most of it

---

### Post by niteshifter on 2009-07-19
Hi,

Yes, you can install a driver within windows to access Ubuntu-side files. I don't have the URL to that site, but a search in these forums on "windows ext3 driver" should get you the link. Another common practice is to use an external drive - USB flash or hard disk - to use as a common area.

---

### Post by hello2007 on 2009-11-15
hi i was going to make a thread about my question but its simliar to this thread so im going to ask it here

when i surf the net and download stuff while using ubuntu cd  or ubuntu usb does any information get stored on the cd or usb after shutdown

---

### Post by efflandt on 2009-11-16
Any record of web surfing you do from live CD would be gone when you shut down.  If you download something, you would need to put it on hard drive or USB or other memory (SD, etc.) if you wanted to save it.  There is a way to have persistent data with live CD if you have a suitably formatted Linux partition with the label "casper-rw" in small letters.

If you use USB Startup Disk Creator, you can allot a certain amount of USB memory for persistent data.  Then it would keep configuration settings, other packages you install, files you download, and a record of your surfing in a virtual ext3 filesystem (casper-rw file on the USB).  The casper-rw file can be loop mounted on another Linux system if you want to access that data when not booted from that USB.

For example if you have 4 GB USB and use startup disk creator to put live/install iso and 2.1 GB persistent data, Windows could still use the remaining 1 GB vfat space to write/read files.  On 2 GB USB you can have 1.1 GB of persistent data (if you try to use all 1.2 GB, it will fail).  So make sure that persistent data slider is down at least 1 click from maximum.

---

