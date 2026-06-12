---
title: "My 8 GB USB"
date: 2012-07-16
forum: Desktop Environments
---

### Post by tfernandes on 2012-07-16
Hi all,

i've installed ubuntu 12.04 LTS on my 8 GB usb. Works fine. 

I tried to install microsoft lync 2010 client using wine but a popup appeared "You have only 350 MB on your hard drive". I cancelled the installation. 

Just wanted to know if there is a disk utility to check the usage on the 8 GB USB. I have not installed anything extra only skype, teamviewer, empathy. 

kindly assist as to why the 8 GB is also so less.

maybe i need to move to 16GB usb. If yes, then how to restore all the apps installed on the 8gb to the new 16GB if i think of moving.

regards,
tfernandes

---

### Post by Shadowstripe on 2012-07-16
you can open a console and use the command df

---

### Post by lukeiamyourfather on 2012-07-16
While Ubuntu can be installed and run from such a small device I wouldn't recommend it. A hard disk is much better if that's an option. If you're going to go the USB flash drive route I'd get at least 32 GB (around $25).

---

### Post by tfernandes on 2012-07-16
> **lukeiamyourfather said:**
> While Ubuntu can be installed and run from such a small device I wouldn't recommend it. A hard disk is much better if that's an option. If you're going to go the USB flash drive route I'd get at least 32 GB (around $25).
hi luke,

thanks for the reply. 

in my case i've already installed the updates, programs on the 8 GB 

can i ghost the USB to a 32 GB?

i dont want to re-install all apps back to the 32 GB USB

Regards,
thads.

---

### Post by Futurian on 2012-07-16
You might also consider getting a USB 3.0 flash drive. Even on a USB 2.0 port it may be substantially faster, your Linux more responsive, than a USB 2.0 drive.
I use an ADATA 16GB USB 3.0 flash drive, which I selected because of a relatively low failure rate reported in reviews. (I do plan to keep it backed up on a hard drive.) Lubuntu is pretty responsive on it, much more so than any *buntu distributions I have on USB 2.0 flash drives.
Good luck!

---

### Post by chocklet on 2012-07-16
Although I'd personally need more space for a satisfying Ubuntu installation, I'm surprised that you can't make it work in 8GB if you are careful, and not a gamer.  If you store many large data files (videos?) in your home directory, you might use a second storage device for your files.

du is useful to see how your storage space is being used.  I am no expert, but you can open a terminal, and start by navigating to home and using...

du -h --max-depth=1 | sort -n

Someone may suggest a better use of du and where to look.  sudo may be required.

---

### Post by lukeiamyourfather on 2012-07-16
> **tfernandes said:**
> 
can i ghost the USB to a 32 GB?


Not sure how that would work with the persistent data. If it were a traditional install on a hard disk it would be easy but USB flash drives are another story.

> **tfernandes said:**
> 
i dont want to re-install all apps back to the 32 GB USB


Why? Bandwidth limitation, time it takes to reinstall, something else?

---

### Post by lukeiamyourfather on 2012-07-16
> **chocklet said:**
> Although I'd personally need more space for a satisfying Ubuntu installation, I'm surprised that you can't make it work in 8GB if you are careful, and not a gamer.  


It does work, you just filled it up with stuff. The Ubuntu install itself is less than 2 GB.

> **chocklet said:**
> 
Someone may suggest a better use of du and where to look.  sudo may be required.

Look at Baobab, its a graphical utility that's much more intuitive than du.

---

