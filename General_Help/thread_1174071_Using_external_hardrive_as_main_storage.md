---
title: "Using external hardrive as main storage?"
date: 2009-05-30
forum: General Help
---

### Post by luxe on 2009-05-30
Hi guys,
I'm an ubuntu newbie (I have 9.04) installed on my pc. I downloaded ubuntu using wubi, to my external hardrive which is 1 TB large. I wanted to use it as my main storage/hardrive, but it seems that my files are downloading/saving to some other space (host/ubuntu/disks/root.disk and that space is 98% occupied. Im not even sure where this space is b/c my primary hardrive is 80% occupied, while my external drive is 9% occupied. (Checking System Monitor file systems).

Its causing a few problems: occasionally synaptic manager won't open (.Xauthority) unless I go an delete some things, and my files won't save or download completely.

My question is - how can I go about changing where my files are automatically downloaded/stored/saved? I tried using edit>preferences> Save files to____ in firefox- but this doesn't seem to help. I just want to be able to save and store things automatically on my external hard drive primarily.

Can anyone help? thanks,
luxe

---

### Post by Cracauer on 2009-05-30
The problem here is simple:

Do you trust all the hardware in the chain (all the USB chips and converters)? They are the cheapest bidder and unlike the harddrive controller chip they aren't on the radar for reliability testing by the vendors.

Do you trust all the drivers, the whole chain? Do you think each of the many more layers you will have to go through is entirely watertight? Remember than when some of USB stuff was written the developer didn't think of critical data, he thought of mice and scanners.

Remember that all this is on the south side of the filesystem<->raw-device barrier. Every error here can random corrupt things, and really randomly, a new write can hit some directory or the superblock or something and nuke files you didn't even touch for years.

---

### Post by zaphod777 on 2009-05-30
> **luxe said:**
> Hi guys,
I'm an ubuntu newbie (I have 9.04) installed on my pc. I downloaded ubuntu using wubi, to my external hardrive which is 1 TB large. I wanted to use it as my main storage/hardrive, but it seems that my files are downloading/saving to some other space (host/ubuntu/disks/root.disk and that space is 98% occupied. Im not even sure where this space is b/c my primary hardrive is 80% occupied, while my external drive is 9% occupied. (Checking System Monitor file systems).

Its causing a few problems: occasionally synaptic manager won't open (.Xauthority) unless I go an delete some things, and my files won't save or download completely.

My question is - how can I go about changing where my files are automatically downloaded/stored/saved? I tried using edit>preferences> Save files to____ in firefox- but this doesn't seem to help. I just want to be able to save and store things automatically on my external hard drive primarily.

Can anyone help? thanks,
luxe

go to accessories and disk usage analyzer it will tell you where all of your disk usage is.

---

### Post by luxe on 2009-05-30
Hi zaphod,
I ran that, and apparently my "filesystem" is near 100% 
distributed amongst:
media 42.9%, 
host 27.4%, 
home 19.4% and 
usr 8.6%) 


But my question is, on which hard drive is the 'filesystem' being stored. And can I move it to my 1TB external hardrive so that there's ample space? If so, how? The "host" folder appears to be the location of my 1tb external hard drive- but that means that it is under my filesystem and counted as space taken up there, instead of providing extra space for file storage. I don't know if I am making sense?

---

### Post by luxe on 2009-05-30
> **Cracauer said:**
> The problem here is simple:

Do you trust all the hardware in the chain (all the USB chips and converters)? They are the cheapest bidder and unlike the harddrive controller chip they aren't on the radar for reliability testing by the vendors.

Do you trust all the drivers, the whole chain? Do you think each of the many more layers you will have to go through is entirely watertight? Remember than when some of USB stuff was written the developer didn't think of critical data, he thought of mice and scanners.

Remember that all this is on the south side of the filesystem<->raw-device barrier. Every error here can random corrupt things, and really randomly, a new write can hit some directory or the superblock or something and nuke files you didn't even touch for years.

I'm sorry- I don't understand at all.

---

### Post by luxe on 2009-05-30
Anybody? :(

---

### Post by Cracauer on 2009-05-31
> **luxe said:**
> I'm sorry- I don't understand at all.

I don't think you should put your important data on a USB drive then.

---

### Post by luxe on 2009-05-31
> **Cracauer said:**
> I don't think you should put your important data on a USB drive then.

What I didn't understand was the point you were trying to make and how it answered my question? Could you clarify that please? Thank you.



Per my original question- could this be a partition issue for my external hard drive?

---

### Post by Cracauer on 2009-06-01
> **luxe said:**
> What I didn't understand was the point you were trying to make and how it answered my question? Could you clarify that please? Thank you.


What I am saying is that if you compare normal harddrives and USB drives than the latter have a lot more hardware and software in the chains that your data passes through. And some or much of that hardware has not been developed with data safety in mind. People working on harddrive controllers and harddrive controller software know they play with your real data. Some or many USB developers might have thought of mice and scanner.

I cannot tell you whether this is a problem in practice, nobody can. So you have to make a guess on your own.

Myself, I am very suspicious of USB chips in particular. Many of them are cheap junk.

As I said earlier, flipping a couple bits in the USB layers while writing data can have catastrophic consequences for the target filesystem, including loss of data you didn't even touch for months.

> **luxe said:**
> 
Per my original question- could this be a partition issue for my external hard drive?

Now I can't understand what the question is :)

---

