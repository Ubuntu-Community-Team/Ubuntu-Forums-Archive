---
title: "Is Promise tx2 133 Ultra ATA card supported?"
date: 2006-01-05
forum: General Help
---

### Post by rgecke on 2006-01-05
The hard drive in question is a Maxtor 60GB.  The motherboard is a Compaq 5000.  It begin bluescreening in Windows so I assumed a dying HD and tested in another PC and it accepts a 5.10 install.  So now I think onboard ATA controller.  I disabled the on-board IDE ATA controller and installed a Promise TX2 133 card, which the BIOS recognizes.  Breezy installs up to the beginning of Base Install and then reports, roughly, "debootstrap has failed, returning error 1" and offers to back up to the previous install step, etc.  I see no drivers for the TX2 at Promise.com and none in ubuntu.com, so I'm concerned.  I'd be willing to disable the advanced features of the card and just go IDE or ATA66 but haven't seen a way to dumb down the card

---

### Post by Dave Gall on 2006-01-22
I notice on the promise web site that there is a bios flash for Linux( presumably for the controller card.)  but no drivers tagged for Linux use.  Googling the net reveals posts that state they us the TX2 with Linux si there must be a way.

I am a newbie with Linux but not PC's.  the instructions for installing Ultra 133 TX2 specifically state that the drivers must be installed prior to installing the controller.  I have sent a request to the Promise support request asking for the correct installation sequence but haven't yet received a reply. I guess I'm just tagging on to your post. if I can get further information I will update you. My hope is that one of those Linux owners with a successful install will see this thread and enlighten us.

---

### Post by breakman on 2006-01-22
I installed Ubuntu 5.10 on my comp and it detected my TX2 133 card. I had no problem reading the NTFS-drive  after mounting it.

---

### Post by Dave Gall on 2006-01-24
Great!  On the install did you just insert the card and attach the led and hdd cables or was there any drivers required?  Sorry if this seems basic!

---

### Post by breakman on 2006-01-25
No drivers requirerd, it just worked after my standard installation.

---

### Post by Dave Gall on 2006-01-28
Thanks  followed in your footsteps  and the system came up recognizing the entire drive . An added bonus was that the internet connection was enabled something that was to be the next problem to be addressed.  Next trying to solve the sound card problem!  Thanks again
:D

---

