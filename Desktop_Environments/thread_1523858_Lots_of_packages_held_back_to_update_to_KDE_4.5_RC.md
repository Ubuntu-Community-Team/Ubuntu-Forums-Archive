---
title: "Lots of packages held back to update to KDE 4.5 RC1..."
date: 2010-07-04
forum: Desktop Environments
---

### Post by Izobalax on 2010-07-04
Word up ya'll...

Currently have a separate partition on my HDD running Kubuntu Lucid. I'm interested in trying out the KDE 4.5 RC1 packages so I've added the necessary repo, as described on the kubuntu website. Problem is, LOTS of packages are being held back, which would obviously result in an incomplete upgrade. First I used my normal command to update the system:
```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

And when that told me about packages being held back, I used aptitude (as this usually is very good at sorting out dependency problems):
```
sudo aptitude upgrade
```

But even aptitude cannot give me a complete upgrade. 

How do I resolve this?

/izo\

---

### Post by nilarimogard on 2010-07-04
sudo apt-get dist-upgrade

---

### Post by Izobalax on 2010-07-04
> **nilarimogard said:**
> sudo apt-get dist-upgrade


Beautiful. Thank you!

/izo\

---

