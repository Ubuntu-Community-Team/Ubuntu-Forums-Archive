---
title: "Adding Text-Mode option to Desktop CD"
date: 2007-06-12
forum: Development CD/DVD Image Testing
---

### Post by Cows on 2007-06-12
Originally I was talking about this idea in this thread <a href="http://ubuntuforums.org/showthread.php?p=2782036#post2782036">here</a>.

Now what I want to do is exactly as the title says which is adding the text-mode feature from alternative cd to the desktop cd. This will enable me to boot up a gui or text mode anything time I want via cd. A optional option is to add the server install ( core ) to the cd.

Now I have been analyzing both the Desktop CD and the Alternative.

**Desktop CD**
- Boots up DEFAULT /casper/vmlinuz

```
LABEL live
  menu label ^Start or install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
```

- Notice the boot=casper and splash

- There's a casper folder in the Desktop CD for the vmlinuz <-- boot ?

**Alternative CD**
- Boots up DEFAULT /install/vmlinuz

```
LABEL install
  menu label ^Install in text mode
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz quiet --

```

- Notice there's no boot=casper and no splash ( no splash screen )

- There's no casper folder but the casper content has been moved over the the /install directory.

My hypothesis is that the vmlinuz or something in the /install folder of the alternative is different then what's in the /casper folder of the Desktop CD. 

I have been trying to burn a BOOTABLE .iso file with the same symlinks etc as the Alternative but I cannot get it to boot using brasero ( burn data cd ) .. I looked for a Make CD Bootable option but that doesn't work neither.

Also brasero filters out the symlinks and hidden files .. I disabled the Brasero to filter out the hidden files and symlinks but for some reason it still thinks that the /ubuntu symlink is a broken symlink and is filters it out anyways.

Any help?

---

### Post by Cows on 2007-06-13
Responses are appreciated :).

---

