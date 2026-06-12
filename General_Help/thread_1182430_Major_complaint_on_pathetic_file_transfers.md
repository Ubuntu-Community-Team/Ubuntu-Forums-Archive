---
title: "Major complaint on pathetic file transfers"
date: 2009-06-08
forum: General Help
---

### Post by VastOne on 2009-06-08
As a huge fan and salesman of Ubuntu, I have a major complaint.  I have been a solid user since Feisty and know my way around and when I don't know an answer have relied on the pro's here.

I recently built 2 new computers and needed to transfer files from another new one to these 2. 40 gig, no big deal.

1st method 2 8 gig USB's It is amazing how poor Jaunty see's these things and how bad they can be. It would take hours to fill one up and then seconds to transfer to the new computer. I corrupted both of these somehow and needed to reformat them

I tried SSH and understand why it is so slow do to the encryption. But why does FTP take 23 hours over a 100 meg pipe? in the same room?  I could have dloaded them faster if they were on line

So I decide to burn it all to dvd's and here is the root of the issue

It is the reading of the files from nautilus that takes forever and a day. I have 40 gig of music and videos, nothing major about 10000 files. But getting them to read and then transfer to Brasero took forever.

In the end, 48 hours later, I got it done.  2 bad blown up usb's and wasted dvd's I am done...

I should have just taken the drives out and put them in the same machine and been done....

But on the other hand, why should I have to do that?

All of these are brand new WD SATA's, the best you can get...

VastOne

---

### Post by Wiebelhaus on 2009-06-08
There's a bottleneck somewhere , I'm using Ubuntu Desktops and Servers on home & work networks without this issue your describing and as a matter of fact , Ubuntu out performs any other platforms on the network.

---

### Post by VastOne on 2009-06-08
> **Wiebelhaus said:**
> There's a bottleneck somewhere , I'm using Ubuntu Desktops and Servers on home & work networks without this issue your describing and as a matter of fact , Ubuntu out performs any other platforms on the network.

I would agree but these were all three separate machines with 3 different builds of Jaunty. And everything else is flawless as far as I am concerned. I even used different routers with the same results. 

This is a simple task, copying files from ne machine to another...

---

### Post by Wiebelhaus on 2009-06-09
> **VastOne said:**
> I would agree but these were all three separate machines with 3 different builds of Jaunty. And everything else is flawless as far as I am concerned. I even used different routers with the same results. 

This is a simple task, copying files from ne machine to another...

Are you using Samba with a traditional setup? There has to be something a miss here , Ubuntu is famous for it's fantastic transfer rates ya know.

---

### Post by VastOne on 2009-06-09
> **Wiebelhaus said:**
> Are you using Samba with a traditional setup? There has to be something a miss here , Ubuntu is famous for it's fantastic transfer rates ya know.

No..Stayed away from Samba as I wasn't looking at long term needs with it an it seemed more to bite off on setting it up for what I needed

Edit:

But I will setup Samba now and try it to solidify your statements.

Thank you

---

### Post by VastOne on 2009-06-13
Ended up setting up NFS and you were correct about Ubuntu speed, it is incredible at 11-12 meg a second.

I could have done this earlier and not felt the pain, but it is good to know the things you cannot do as well.

---

