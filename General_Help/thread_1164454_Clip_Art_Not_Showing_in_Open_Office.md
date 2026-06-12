---
title: "Clip Art Not Showing in Open Office"
date: 2009-05-19
forum: General Help
---

### Post by s.fox on 2009-05-19
Hi,

I followed [this]("https://help.ubuntu.com/community/ClipArt") guide on installing clip art for open office.  I followed all the steps in the instructions but non are shown in the gallery. 

Can anybody advise me on what to do?

Many thanks,

-Ash R

---

### Post by s.fox on 2009-05-21
1 day bump.

---

### Post by s.fox on 2009-05-23
24 hour bump

---

### Post by s.fox on 2009-05-25
Two day bump :(

---

### Post by DeMus on 2009-05-25
> **Ash R said:**
> Hi,

I followed [this]("https://help.ubuntu.com/community/ClipArt") guide on installing clip art for open office.  I followed all the steps in the instructions but non are shown in the gallery. 

Can anybody advise me on what to do?

Many thanks,

-Ash R

I have just done the same and it works. I just changed the ln line to make a link to the right folder into:
sudo ln -s /home/jan/png /usr/lib/openoffice/share/gallery/cliparthome
(where jan is my username).
Do the same and look in your home folder to follow the link to the right folder where all the cliparets are put.
Have fun

---

### Post by Scarletgecko on 2009-05-31
I have the issue as describe above.  Original path is correct per add/remove programs install.  The files are there, just not visible to in the Open Office Gallery.

---

### Post by jmszr on 2009-05-31
Scarletgecko,

In OpenOffice Writer (for example) make sure that Tools > Gallery is checked.
Then, directly above the numbered sizing bar (or whatever it's called) between the 3 and 4 inch marks is a short dotted line. Click on that and then by moving the mouse up and down a two-headed arrow will appear - hold down your left mouse button and drag the arrow down at least a couple of inches and that should reveal the gallery.
Right click on the item and you can insert it.
It's the same in Draw, but more fun as you can do more with it. Of course you may already know this and have an entirely different issue. Then never mind.

---

### Post by Scarletgecko on 2009-05-31
Thanks for the reply.  I have the gallery open (see snapshot).  The clipart does not appear in the gallery.  I Have checked the file locations and they are correct.

What next?

---

### Post by jmszr on 2009-05-31
Scarletgecko,

I'm running 8.04 and OpenOffice 2.4.1 so I can't be positive about your setup. I really don't know. (grasping at straws) Check Synaptic and see if it is actually installed... check OO.o Extension Manager to make sure "OOOP-accessories-(nonfree-)2.6.0.2.oxt" is enabled. There are both free and nonfree gallery extensions. Otherwise I don't know what to suggest.

---

### Post by Scarletgecko on 2009-05-31
The files are there.  I can navigate manually to them from the gallery load, but an only see one file at time by filename (no thumbnails).  It appears that the link created with 

sudo ln -s /usr/share/openclipart/png/ /usr/lib/openoffice/share/gallery/clipart

should create entry in the Gallery menu for the clipart does not work.

-p

---

### Post by ricardisimo on 2009-06-02
Here's the problem, I guess: [https://bugs.launchpad.net/ubuntu/+source/openclipart/+bug/375878](https://bugs.launchpad.net/ubuntu/+source/openclipart/+bug/375878)

Adding your voice to bug reports is normally the best way to get it worked on.

The other option is to add all 22 subfolders of /usr/share/openclipart/png and /usr/share/openclipart/svg as new themes (on the left of the Gallery.) It'll take a while, but it'll probably still be quicker than waiting for a bug fix. The third option - and I doubt it's a very good one - is simply to add one single New Theme titled "Openclipart" that draws from /usr/share/openclipart. I'll be avoiding that one unless someone else is willing to be the guinea pig.

---

### Post by ricardisimo on 2009-06-02
Oops! That was a duplicate bug. Here's the master: [https://bugs.launchpad.net/ubuntu/+source/openclipart/+bug/363712](https://bugs.launchpad.net/ubuntu/+source/openclipart/+bug/363712)

It'll be fixed in Koala, evidently.

---

