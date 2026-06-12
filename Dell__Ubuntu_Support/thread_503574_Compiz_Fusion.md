---
title: "Compiz Fusion"
date: 2007-07-18
forum: Dell  Ubuntu Support
---

### Post by Ryuusen on 2007-07-18
I don't know if it's a dell only thing, but i just installed ubuntu fiesty on my inspiron 6400, everything is working fine. i went to install compiz fusion using one of the guides here. On the last step i got a line that said "checks indicate that it's impossible to start compiz on your system". i'm using a mobile ati radeon x1400. in the device manager it's listed to be an unknown device type and have unknown capabilities. any ideas on a fix?

---

### Post by Paul S on 2007-07-26
> **Ryuusen said:**
>  i'm using a mobile ati radeon x1400.

The ATI fglrx driver does not support composite by itself, so you have to install xserver-xgl and get it working to have the composite that's needed for compiz.  There are howto's available in the ubuntu wiki, the old compiz.org site and the old beryl-project site on your specific card.  It's a pain, but once done, it will work.  Another alternative is to buy a replacement nvidia geforce go 7300 from dell and swap it out yourself .. they have a good service manual with all the details well documented.  That's what I did.  On nvidia, the linux driver supports composite out of the box.

Trevino has a good set of frequently updated compiz-fusion packages for feisty and I'd recommend using them.  Just search his name to find out how to set it up.

HTH

---

