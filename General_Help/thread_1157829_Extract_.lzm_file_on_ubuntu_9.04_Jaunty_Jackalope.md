---
title: "Extract .lzm file on ubuntu 9.04 Jaunty Jackalope???"
date: 2009-05-13
forum: General Help
---

### Post by Safwan Khan on 2009-05-13
I have been trying hard to find out some way to extract .lzm file to a directory or to convert it to some other common compressed archive format but it has been a miserable failure for me so far. :( Please tell me what do I need to do? I have read on a forum that slax package manager is required to unpack it (I may have read wrongly, kindly correct me) but I am running Jaunty Jackalope. Any help would be greatly appreciated.

P.S., This is my first thread on ubuntu forums. I have recently migrated from Windows to Linux and I ain't turning back.:)

---

### Post by KhurramM on 2009-05-13
Thru my default packaging of hardy

Right click and goto extract here

This should work.

Or try:

[http://www.linuxquestions.org/questions/linux-software-2/how-do-i-decompress-lzm-files-586399/](http://www.linuxquestions.org/questions/linux-software-2/how-do-i-decompress-lzm-files-586399/)

---

### Post by Safwan Khan on 2009-05-13
There is no option like "extract here" for .lzm files in ubuntu 9.04 Jaunty Jackalope. And the link that you posted is not for my version.. I don't know how to work things out.. Please someone help me. I usually always solve my problems by surfing through the forums but this one is a real hard nut to crack... any help would be highly appreciated.

---

### Post by igoor on 2009-05-13
```
aptitude install squashfs-tools
```

```
unsquashfs -f -dest existing_output_directory source_file.lzm
```

---

### Post by Safwan Khan on 2009-05-14
Thanks a lot for your response! :p
I finally figured it out myself and you confirmed it! :D

Thumbs up! Cheers!!!

---

### Post by leonidus on 2009-05-28
dear friends is their any to extract .lzm file in ubuntu server 8.1

---

### Post by Kangarooo on 2010-06-06
Thas not working for me
IZM$ ls
w1.lzm  a2.lzm  p3.lzm  p3.lzm.lzma
i installed and used
lzma p3.lzm
and that made p3.lzm to disapear and to make p3.lzm.lzma
from new file i could open that with archiver and extract the same p3.lzm back out
so i tryd as u say
unsquashfs -f -dest / p3.lzm
 and got this error : Can't find a SQUASHFS superblock on p3.lzm

So what would work?

---

