---
title: "Using Old Computer as Storage Space"
date: 2009-06-01
forum: General Help
---

### Post by Musicologynut85 on 2009-06-01
I was cleaning out my grandmother's closet the other day and found enough old computer parts in there to build another computer... so, I went out and bought a tower from a garage sale and did.

I have two hard drives in it and 256K of RAM (on a single stick, I could not find two matching ones, so I used the highest single).

The hard drives are 2 and 4 GBs.

I'm planning on throwing a linux distro on there and using it as extra storage space for the many .pdf files (musical scores) that I've accumulated over the years and some other random things.

Are there any good suggestions in terms of set-up for this? Ideally, I want to be able to plug the server into my laptop (Ubuntu Jaunty) via USB and mount it like any other drive... but I know that might be more complicated than it's worth.

I currently have a DSL boot disk in the tower, but nothing is actually written to the hard drive yet.

Thanks,
Jeff

---

### Post by madverb on 2009-06-01
You could have just bought an 8GB USB drive for the same as you bought the case...

---

### Post by PGScooter on 2009-06-01
> **madverb said:**
> You could have just bought an 8GB USB drive for the same as you bought the case...

but that would not have been as fun, adventurous, or instructive! :)

sorry Musicologynut85, I don't have any enough knowledge to advise you. But good luck!

---

### Post by seydou on 2009-06-01
> **Musicologynut85 said:**
> ... I want to be able to plug the server into my laptop (Ubuntu Jaunty) via USB and mount it like any other drive... 

I kinda like the attitude of re-using old stuff, even though the storage space in this case is far from being impressive ;-) Anyhow, I would probably put a network card into that and use nfs to share the filesystem - that is what I do in my home network. If you do not want to play with mounting network drives, you might opt for ftp as well. As for the setup, beare minimum with nfs support, ssh for remote admin, ftp server and no X sever. You might consider setting up samba to open that for windows world, if needed. If you use DHCP to set yout laptop's IP, also install dhcp server on the storage box.

---

