---
title: "Nautilus doesn't recognize my blanc media"
date: 2005-02-26
forum: Desktop Environments
---

### Post by martijntje on 2005-02-26
I have a really strange problem. When i try to burn a dvd image to an empty dvd, nautilus keeps telling me to insert a blanc media.

Now i *know* that they are blanc. I only removed the plastic a minute ago, so unless someone burned them from a distance, they are empty.

The discs should be able to take up to 4.7 GB of data, the image file is only 4.4 GB, so that shouldn't be the problem.

I created the image myself with mkisofs, so i know the image is OK.

I'm doing exactly the same thing as the last time i had ubuntu on this computer (i reinstalled it on a new 10.000 rpm SATA drive), and it always worked like a charm for me.

OH: these are my HW specs:

- Asus K8V Deluxe motherboard
- AMD Duron 64 3200+
- 2 GB Corsair memory (don't know exact specs)
- Raptor 74 GB 10.000 rpm SATA drive.
- Some other HD's
- Some old CD-rewriter
- Plextor DVD Rewriter
- Some other CD drives
- More stuff

And yes, i did select the correct drive from the dropbown box to write to.
Anyone have any idea?

---

### Post by illek on 2005-02-26
I had the same problem until I ran apt-get dist-upgrade.  That fixed it for me.  Good luck.

---

### Post by martijntje on 2005-02-26
Doesn't do anything for me.
It didn't update any packages.

---

### Post by martijntje on 2005-02-26
When i boot from my non-SATA disc it does work...

Apparantly SATA is the troublemaker here.

---

