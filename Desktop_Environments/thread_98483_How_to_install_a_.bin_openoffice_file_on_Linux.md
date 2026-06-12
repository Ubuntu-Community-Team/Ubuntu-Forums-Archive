---
title: "How to install a *.bin openoffice file on Linux"
date: 2005-12-03
forum: Desktop Environments
---

### Post by pfabrikant on 2005-12-03
Hey,
I'm new with linux so forgive my basic questions..
I downloaded a hebrew version of openoffice for Linux from openoffice.org website. It's a *.bin file format and I don't know how to install it through linux.. I tried synaptic package manager but it didn't recognize the file format. I don't have a clue how to use the terminal, so..I'll really apreciate some help. Thanks !

---

### Post by flopsy on 2005-12-03
cd /path/to/file
chmod +x filename.bin (makes the file executable)
sudo ./filename.bin

EDIT: Sorry for the terseness.

Open a terminal: Applications > Accessories > Terminal
Enter the following files, followed by the Enter key. Replace filename.bin with the name of the file you downloaded.

```
cd ~/Desktop (I'm assuming you downloaded with Firefox)
chmod +x filename.bin
sudo ./filename.bin

```

If you didn't download with Firefox, or have subsequently moved the file, you can find it by entering find ~ -name *.bin, followed by enter.

---

