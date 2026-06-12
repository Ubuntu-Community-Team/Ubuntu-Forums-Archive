---
title: "Laptop install"
date: 2009-03-02
forum: General Help
---

### Post by The_Cavester on 2009-03-02
Hello all.
I have a laptop that I am trying to make secure.
I would like to make it so that with out the right usb flash drive
the laptop will not boot. Not at all.
Using a live install on a usb key would work but any one can
make one of those and get into my laptop.
Any ideas would be awesome.
or even a link or two to get me started would also be great.
I just don't know were to start.
Help, help

---

### Post by brian_p on 2009-03-02
> **The_Cavester said:**
> 

I just don't know were to start.
Help, help

With physical access to the machine security is severely limited or non-existent. Perhaps the best you can do is turn off booting from usb flash in the bios and password protect it.

---

### Post by The_Cavester on 2009-03-02
Thank_you Brian_P for your reply.
I think you may have misunderstood what I am trying to do.
I would like to make it so that with the right USB drive
the laptop boots just fine but with out it the machine is
dead in the water.
Maybe encrypt the key and encrypt grub or something?

---

### Post by brian_p on 2009-03-02
> **The_Cavester said:**
> Thank_you Brian_P for your reply.
I think you may have misunderstood what I am trying to do.
I would like to make it so that with the right USB drive
the laptop boots just fine but with out it the machine is
dead in the water.
Maybe encrypt the key and encrypt grub or something?

I don't think I have misunderstood what you are trying to do. The bios will boot from a usb drive, CD etc whether it is yours or not. Having **your** drive or grub encrypted is neither here nor there.

---

### Post by sgosnell on 2009-03-02
Not possible.  The best you can do is remove the HDD, and keep everything on the flash drive.  That way if someone does get the laptop, they can't get any data from it, because there is none there, and a laptop without a HDD isn't worth much to most people.  As long as there is a BIOS, it's possible to boot it from something, but if there is no data to get it doesn't make much difference.  If you're really worried about security, encrypt the flash drive with truecrypt, so that if someone get it, they can't easily recover anything.

---

