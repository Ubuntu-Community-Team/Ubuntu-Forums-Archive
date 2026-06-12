---
title: "Install Windows after Ubuntu is installed."
date: 2006-09-08
forum: Desktop Environments
---

### Post by drews_blunted on 2006-09-08
Hello! I have ubuntu installed on my 120 gig 7200 rpm ata hard drive. i would like to make a 10 gig partition and install windows on to the hardrive. what i am woundering is how can i install windows now that ubuntu is already installed. I heard somewhere that windows will only install onto the begining or primary part of your hardrive, where ubuntu is already installed or something similar to that. Is this true and if so what are any possible work arounds.

---

### Post by pufuwozu on 2006-09-08
No, Windows will overright your hard-drive's MBR. This means that you'll no longer have the Grub boot loader.

To fix this you'll need to reinstall Grub after you've installed Windows. Look at the official documentation to see how to do this:

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html")

---

