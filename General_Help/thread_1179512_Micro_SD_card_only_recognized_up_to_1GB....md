---
title: "Micro SD card only recognized up to 1GB..."
date: 2009-06-05
forum: General Help
---

### Post by ChocoTuar on 2009-06-05
I have a microSD card that's listed as 2GB hooked up to my USB 6-in-1 reader through an adapter and I'm trying to partition/load files onto it. The problem is that ubuntu 9.04 and gparted only recognize the card as being 1 GB, so when I try to format an ext2 partition on it, the whole thing gets messed up. I have over 1GB worth of data to put on there, so this is a very big problem. I've tried this on many 2GB cards with the same results (and a 512MB card that was recognized perfectly).

Would anybody know why it's saying a 2GB card is only 1GB?

---

### Post by yoman82 on 2009-06-05
Some older readers are not compatible with higher density cards, and simply will not recognize them. If this is the case, you'll probably need to use new equipment. Is there any way you can test the card on another computer or reader.
Otherwise, is the SD card split into two partitions and being recognized as two drives?

---

### Post by fragos on 2009-06-06
I had a similar experience when I tried to format a 16Mb FAT SD card. I ended up with 8Mb ext2. From that point on the card stayed at 8Mb even when using Gparted to reformat the card to FAT. Don't forget that formating an SD card to ext2 will make it unusable on Windows, PDA's, cameras and MP3 players.

---

### Post by ChocoTuar on 2009-06-24
I figured it out... turns out the multi-reader I was using wasn't reading it correctly, or something. I plugged the same card into a laptop with an SD card reader built-in and it worked fine.

---

