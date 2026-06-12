---
title: "Optimum Partition Setup help"
date: 2009-04-17
forum: General Help
---

### Post by Scubdup on 2009-04-17
I want to install Jaunty and Ext4 to try and get the fastest boot times and general speed out of my machine as possible.

Having done a bit of reading I'm thinking of partitioning my 200Gb HDD as follows:-

Boot Primary (1Gb) 'Ext4', set to mount to ‘boot’
Swap Primary (4Gb) 'swap’ or ‘swap area’
Root Primary (45Gb) 'Ext4', set to mount to ‘/’
Home Primary (the rest - 50Gbish) 'Ext4'

Does that seem sensible?

---

### Post by Bachstelze on 2009-04-17
> **Scubdup said:**
> 
Boot Primary (1Gb) 'Ext4', set to mount to ‘boot’

I know hard drives are cheap nowadays, but that's uselessly big. 512 MB will already be far more than enough.

> **Scubdup said:**
> Root Primary (45Gb) 'Ext4', set to mount to ‘/’

Likewise. Make it 10.

---

### Post by Scubdup on 2009-04-17
OK. Sounds sensible.

Boot Primary (0.5Gb) 'Ext4', set to mount to ‘boot’
Swap Primary (4Gb) 'swap’ or ‘swap area’
Root Primary (10Gb) 'Ext4', set to mount to ‘/’
Home Primary (the rest - 185Gbish) 'Ext4'

What do you think about the Swap partition - I'd like to be able to hibernate if poss.

Also what about ext4? Is it worth doing for boot,root, and home?

---

### Post by Bachstelze on 2009-04-17
> **Scubdup said:**
> What do you think about the Swap partition - I'd like to be able to hibernate if poss.

If you want to hobernate, your swap must be at least as large as your RAM. How much RAM do you have?

> **Scubdup said:**
> Also what about ext4? Is it worth doing for boot,root, and home?

I can't really tell you about ext4, I have not used it myself yet. I doubt you would see any noticeable difference for everyday use, though.

---

### Post by meeko on 2009-04-17
I'd be careful with ext4 and Jaunty. Admittedly I have not tested it myself, but the website warns of kernel panics and other issues involving ext4 that are not yet resolved.

[http://www.ubuntu.com/getubuntu/releasenotes/904overview#Known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/904overview#Known%20issues)

---

### Post by Scubdup on 2009-04-17
Thanks. Maybe I'm better off staying with Ext3 for a bit then.

---

