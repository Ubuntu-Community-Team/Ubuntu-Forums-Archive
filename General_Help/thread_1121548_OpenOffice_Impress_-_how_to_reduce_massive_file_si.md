---
title: "OpenOffice Impress - how to reduce massive file size?"
date: 2009-04-10
forum: General Help
---

### Post by Cosmogirl on 2009-04-10
Hi,

I'm quite new to Ubuntu (we installed 8.10 a few months ago) and I'm hoping someone can help with this.  I have searched on the forum but nobody else seems to have had a similar problem.  I used OpenOffice Impress to make a photo slideshow but the finished file is HUGE (nearly 27MB).  However before inserting the photos (originally 2-3MB) I used GIMP to resize & compress them so that none of them are more than 150KB.  There are no background images in the slideshow, but a little slide / custom animation (photos fade into each other).  There are 43 photos in the show (up to 3 on a single slide) and a few lines of text (short captions on a few photos).

I tried downloading Sun Presentation Minimizer via Synaptic.  It takes me through all the steps leading to minimization but unfortunately when I click 'finish'it causes Impress to crash.

Please help!  Thanks.

---

### Post by frogotronic on 2009-04-16
I think this only works with 2.3

---

### Post by Cosmogirl on 2009-04-21
Thanks for your reply.  We have OpenOffice 2.4, so that might be part of the problem.  However I still don't understand why the file size is so big!

---

### Post by TenPlus1 on 2009-04-21
Inserting photos will always increase the size of a presentation file, but I'm sure you can LINK photos form inside a presentation which keeps the filesize small and the photos external...

---

### Post by Cosmogirl on 2009-04-24
Thanks for the advice.  In fact the problem is that I want the slideshow to be portable (ie emailable) & if possible I'd like to put it on a website at work where the file size would be limited to just a few of MB...  I think I'll have to give up on the idea & just put some basic photos on the site instead.  However as I've already said, I just don't understand why the slideshow is so huge - recently received a similar Powerpoint one which was less than 5 MB.  Well thanks for your help anyway!

---

### Post by Flimm on 2010-02-13
You might want to try exporting to PDF and ticking "reduce image resolution". It reduced a 75MB file to 27MB in my case.

---

### Post by AFD8766 on 2010-04-19
I got the following results using OpenOffice 3.0.1 on Jaunty Jackalope (9.04); exporting a 30-MB Impress file to a pdf; File | Export as PDF |  Options | General | Images

Selecting only lossless compression *increases* file size to 33 MB.
Selecting lossless compression and setting "reduce image resolution" to 300 dpi increases file size to 99 MB (!!)

OK, let's *reduce* file size!  
Selecting only jpeg compression 90%, decreases file from 30 to 11 MB.
Ditto at 70% gets you 6.2 MB; 50% yields 4.6 MB.

OO help gives a description of exporting to pdf and says, with regard to jpeg compression: 
"some pixels get lost and artefacts [sic] are introduced, but file sizes are reduced." 

I didn't check my file for this...

---

