---
title: "Small HD"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Rayston on 2006-07-20
I made the mistake of installing Ubuntu on the smaller of my 2 HD's 5 gigs. Now I am running out of room, currently down to about 600 megs. A few questions. 

1. Is it possible to install things to a secondary HD when installing from synaptic? 

2. Is it possible to just move my entire install to my other HD with no loss of info or functionality? (my guess would be no, but doesnt hurt to ask)

Thanx

Rayston

---

### Post by philippe_carlo on 2006-07-20
The best thing to do is to move a very full part of your installation, like the '/home' directory to the second HD and mount that HD under /home in fstab.

---

### Post by Landoln on 2006-07-20
> **Rayston said:**
> 1. Is it possible to install things to a secondary HD when installing from synaptic? 
Probably not unless you do #2.
> **Rayston said:**
> 2. Is it possible to just move my entire install to my other HD with no loss of info or functionality? (my guess would be no, but doesnt hurt to ask)

Yes, kind of. You'll have to modify the fstab to mount your other hd as /, and if you move your /boot directory to a different partition or device you'll have to modify your /boot/grub/menu.lst file to reflect the change and possibly reinstall grub (if you're using grub).  But I think you could move to a new hd without too much trouble.  I've never tried it, so someone will have to correct me if I'm wrong.  If you try it, just make sure you have a livecd laying around somewhere so you can correct any mistakes if you make any before rebooting.

---

### Post by Rayston on 2006-07-20
so, If I do #2 correctly, synaptic will start to install stuff to my secondary HD? 


So I would have to move my /home directory, tell fstab that I have moved it. and also possibly reinstall grub(I am using grub) is that all? Anyone know of a walkthrough or anything for this kinda thing? 

Thanx

Rayston

---

### Post by aysiu on 2006-07-20
> **Rayston said:**
> 
2. Is it possible to just move my entire install to my other HD with no loss of info or functionality? (my guess would be no, but doesnt hurt to ask) Yes, but you'll still have to edit your /etc/fstab and /boot/grub/menu.lst to reflect the change:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by Rayston on 2006-07-20
oooh, this looks like what I need. So I could backup the image, then "restore" it to my other HD then edit fstab and grub so they know where to look for the image, then I could use my current primary 5 gig for whatever I wanted? 

Thanx

Rayston

---

### Post by Landoln on 2006-07-20
> so I would have to move my /home directory
You would have to move your / directory to accomplish the change you're talking about, not just the /home.
Synaptic doesn't install programs to /home, so if programs are what is taking up most of the space, just moving /home won't really help much.

---

### Post by Landoln on 2006-07-20
> so I would have to move my /home directory
You would have to move your / directory to accomplish the change you're talking about, not just the /home.
Synaptic doesn't install programs to /home, so if programs are what is taking up most of the space, just moving /home won't really help much.

---

### Post by aysiu on 2006-07-20
This will show you how to move your /home directory to its own partition. I'd imagine the process for moving the /usr directory is quite similar.
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

I'm in favor of using PartImage, though.

---

