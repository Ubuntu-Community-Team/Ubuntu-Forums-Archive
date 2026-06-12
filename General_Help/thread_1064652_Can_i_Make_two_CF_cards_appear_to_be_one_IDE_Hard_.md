---
title: "Can i Make two CF cards appear to be one IDE Hard Drive?"
date: 2009-02-09
forum: General Help
---

### Post by Sonic Reducer on 2009-02-09
I just got an Averatech 2100 laptop, and I want to replace the 2.5" IDE hard drive with Flash storage. I found something that seems to be exactly what i need, it's an [Addonics CF Hard Drive Adapter for Notebooks]("http://www.addonics.com/products/flash_memory_reader/ad44midecf.asp").

I can use my employee discount at work to get 8GB CF cards fairly cheap, but if i can't make the two appear as one disk i'll just pony up the cash for a 16GB CF card.

how do i make two CF cards appear as one device?

---

### Post by kerry_s on 2009-02-09
the adapter is suppose to do that, the 2 cards should show as 1 drive.
otherwise i think it would screw up the bios having 2 drives on 1 master.

---

### Post by heindsight on 2009-02-09
> **kerry_s said:**
> the adapter is suppose to do that, the 2 cards should show as 1 drive.
otherwise i think it would screw up the bios having 2 drives on 1 master.

According to that link it would appear one CF acts as master and the other as slave. I might be wrong though, never used one of these...

Is there a particular reason why you want them to appear as one device? 
I'm not sure it's possible to make the two really appear as one device, if it were me, I'd simply use one device as my / filesystem and the other for my /home filesystem. If you really want one filesystem spanning both devices, you could look at using LVM to create a single logical volume spanning both devices (have a look at [http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)).

---

### Post by Sonic Reducer on 2009-02-10
> **heindsight said:**
> Is there a particular reason why you want them to appear as one device? 
I'm not sure it's possible to make the two really appear as one device, if it were me, I'd simply use one device as my / filesystem and the other for my /home filesystem.

having one big partition would be ideal because i want to load some GPS software but i don't know if it would save the maps to my /home or a different directory. one partition basically allows more flexibility for however i want to set it up

---

### Post by heindsight on 2009-02-10
> **Sonic Reducer said:**
> having one big partition would be ideal because i want to load some GPS software but i don't know if it would save the maps to my /home or a different directory. one partition basically allows more flexibility for however i want to set it up

Well in that case, I think LVM is what you're looking for.

---

