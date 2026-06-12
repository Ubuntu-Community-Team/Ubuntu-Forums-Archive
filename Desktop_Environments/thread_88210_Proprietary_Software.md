---
title: "Proprietary Software"
date: 2005-11-09
forum: Desktop Environments
---

### Post by CharlieC on 2005-11-09
I tried to play a DVD I rented from Netflix on my Ubuntu. As I suspected it would not play because I don't have libdvdcss. I have looked for that one and cant seem to come up with it. Even if I found it I would not know where to put it unless I could do an apt-get or something. I did find it in suse 10.0. I think it was part of another program. 
    I have no objection to paying for software. Can someone suggest a program I can purchase so I can play DVD's. I have Ubuntu 5.10.

Thanks
Charlie

---

### Post by Kyral on 2005-11-09
You don't have to purchase (Heck I don't think you can buy something for Linux)

[https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b](https://wiki.ubuntu.com/RestrictedFormats#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b)

That should work

---

### Post by CharlieC on 2005-11-09
Hi;

    Thanks, that did it. 
    I did download a tar and a deb. I did the tar xvzf thing and it worked, unfortunately the DVD still did not play. I then found a .deb file. I tried apt-get and it worked as well. Of course the DVD still did not play. As I said even if I found it I would not know what to do with it. 
    Maybe you could tell me why neither of them worked. I suspect it is a path thing. One of the errors I received was no C compiler in path. 
    Thanks for you help.

Charlie

---

### Post by Kyral on 2005-11-09
Uuuh.....try installing VLC

---

### Post by Leif on 2005-11-09
[QUOTE=CharlieC]Hi;
 One of the errors I received was no C compiler in path. 
[/QUOTE]

sudo apt-get install build-essential

---

