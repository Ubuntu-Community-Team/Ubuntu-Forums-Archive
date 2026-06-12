---
title: "How to remove Linux Partition in Vista? and broken Grub? Ouch!"
date: 2009-06-19
forum: General Help
---

### Post by stevebelden on 2009-06-19
Well, there you go.  I shouldn't have done what I did, but I did, and now I need help recovering from it.  Hope y'all can help.

I've got a Compaq Presario Laptop. 150 gig HDD. I wanted to try Linux out again, so partitioned off 28 gigs and installed Ubuntu. Worked great, except that never could get the wifi working. All was happyhappyjoyjoy until recently when I loaded a lot of material onto the Vista partition and was running out of room. So, thought I'd get rid of the Linux partition for now and give that space back to the Vista side. Apparently, I did it badly and am now deeply regretful.

I turned the Linux partition into "free space" using the Vista Manager. Then found that I couldn't put that "free space" back into the Vista partition - well, *I* couldn't figure it out. Put the computer to sleep for the night, figuring I'd try again in the morning. Which, when I booted it up this morning, I get a Grub Error 17 that I can't seemt to get past. So, I can't load anything. Obviously, I'm not as smart as I thought I was. Grrr...

So. How can I fix these problems? I want to get the "free space" back into the Vista partition and get rid of the Grub loader. For now. I'm planning on getting a dedicated Linux laptop later [IMG]http://http.cdnlayer.com/lq/images/questions/images/smilies/smile.gif[/IMG]

Thanks in Advance very much for any assistance.  

-Steve

---

### Post by sailthesea on 2009-06-19
If you have a VistaCD you should be able to boot in and fdisk to remove Grub and go from there
 Max out the Vista partition and erase the others 
 Put Ubuntu on your new laptop and have fun!:D
 Good Luck and Welcome

---

### Post by stevebelden on 2009-06-19
My machine didn't come with a Vista CD.  Yes, it was brand-new-in-the-box.  Not sure why it didn't come with one.  Oh, wait - apparently, I was supposed to *make* a set of recovery disks.  My bad.  

Any thoughts?  And thanks very much for the reply.

---

### Post by sailthesea on 2009-06-19
You can probably get into recovery mode or BIOS and repair Windows from there but I'm not familiar with that machine so I don't really know how 
Try pressing F8 etc on boot up you may be able to bypass grub and get windows  
 Gotta go to bed Best of luck

---

### Post by stevebelden on 2009-06-20
Thanks very much for your help :)

I did dig out my Ubuntu CD and have that loaded.  Running GParted right now, but not sure what I'm doing with it.  I'll do some reading...

---

### Post by monkey56657 on 2009-06-20
I use bootit-ng for doing basic partition work. 

[http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)

It will allow you to resize your vista partition. You can also then create a standard mbr that will allow vista to boot again (hopefully). 

1. 'Partition Work'
2. 'Create EMBR'
3. 'Undo EMBR'
4. 'View MBR' 
5. Highlight Vista Partition
6. 'Set Active'

^ This generally works for me. 

It's not free software but they offer a trial... that's all you need since you don't need to install it permanently.

---

