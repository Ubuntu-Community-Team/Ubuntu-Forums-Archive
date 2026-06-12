---
title: "NForce2 Board, Do I Need NVIDIA Drivers?"
date: 2006-01-03
forum: General Help
---

### Post by twokatmew on 2006-01-03
I just installed Ubuntu 5.1 today and everything seems to be working fine.  I figured out how to add packages, update using Synaptic, etc.  I'd hoped I wouldn't need to install the NVidia unified drivers or even the driver for my Geforce4 MX card.  BUT... even though I've selected the correct resolution and refresh rate for my LCD monitor, the screen image is shifted to the right.  I can't find any utility to center the image on my monitor.  Am I missing something?  I'm wondering if I might have to install the Nvidia video driver.  I followed the directions in Ubuntu help, but it tells me the files are not there.  Checking the directory listed in the instructions, the file(s) are indeed missing.  So I downloaded the latest video driver from Nvidia, but when I use the "sh <filename>" command to install it, I get a message that binutils is not installed.  (I could have sworn I saw "binutils" go by as packages were installed.)  Or, it says I should make sure the "ld" command is in my path.  I can't find the "ld" command, nor do I know how to edit my path in Linux.  Can someone help?

Thanks!

---

### Post by twokatmew on 2006-01-03
Never mind....  I reread the Ubuntu instructions, and I realized I'd missed the part where I had to download and install nvidia-glx using Synaptic.  Anyway, I did that, and my screen position is properly centered now.  :-)

---

