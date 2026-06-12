---
title: "Need to clarify &quot;re-install operating system&quot; option"
date: 2009-10-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by smallbear on 2009-10-04
Hi, I have a Dell Vostro A840 running Ubuntu 8.04 that it was supplied with.  I need to clarify how the 're-install operating system' option works and if it can be put back onto the system if it gets lost.

Whenever I want to revert to factory install, I choose this option and I do not have to use the original Ubuntu DVD.  Since this is possible without the DVD, if I should wipe the hard disc (for instance when trying another Linux dist.), would it be possible to replace this original Dell facility for re-installing Ubuntu?

Another question I have is that I created a Dell rescue CD using the icon "Create Dell Rescue DVD image" on the desktop, but this does not seem to save any changes I have made, nor save any additional software I have installed.  Is there a way to do this, so that I can recover my own particular configuration from CD, should I need to?

Thanks very much.

---

### Post by Dennis N on 2009-10-04
To preserve changes you have made and software you have added up to some particular point in time, you might want to make an image of your hard disk using a tool such as Clonezilla. It can save a hard disk image (exact copy) to an external drive (one option) which can then be restored to the computer if needed.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by ugm6hr on 2009-10-05
The re-install option uses an image file in a HD partition.  So if you actually completely wipe the HD, you will remove the restore function.

If you only write over the OS partition, you will be able to restore whenever you wish.  However, this restores to factory default, not with your modifications.

As mentioned, there are free options to create a partition / HD image for recovery manually if you want to restore to your current state.

---

### Post by smallbear on 2009-10-07
> **ugm6hr said:**
> The re-install option uses an image file in a HD partition.  So if you actually completely wipe the HD, you will remove the restore function.

Thanks for the information.  Is it possible however, to re-create that 'rescue' partition, if it were to be lost?  For example if the hard drive failed and were to be replaced.  Furthermore, can the 'rescue' partition be re-created by re-installing from the 'recovery' CD that I have created?

---

### Post by tophatandy on 2009-10-07
Im not quite sure how to recreate that backup partition of the hard disk, but i will look into it for you. 

from here, we do have the option of creating a backup 8.04 dvd or usb drive even if you want. you can download the disk image from [here]("http://www.ubuntu.com/GetUbuntu/download"). and from there, you can burn that image with pretty much any burning program, or you can make a bootable usb by using unetboot in, which is pretty self explanitory and can be found [here]("http://unetbootin.sourceforge.net/"). (*note* installing unetboot in will result in data loss on the flash drive) 

in the meantime, i will try to hunt down an answer for you.

---

### Post by smallbear on 2009-10-07
> **tophatandy said:**
> Im not quite sure how to recreate that backup partition of the hard disk, but i will look into it for you.

Many thanks - I appreciate the help very much.  I don't want to lose the convenience of reverting the system back to its original state, as I'm working on testing mailservers at the moment and frequently have to go back!

---

