---
title: "TinyFugue MUD Client Installation"
date: 2006-02-06
forum: Gaming &amp; Leisure
---

### Post by NeoKotoz on 2006-02-06
Hello,
I've been told the Linux community likes to help each other out, so I was wondering if anyone could help me with this. I'm using Ubuntu 5.10 and I've been trying to install TinyFugue so I can go to my textbased games such as the ones I have on windows.

My current problem is when I open the Terminal and go: cd Desktop/tf-50b7 it opens up the directory, then when I go ./configure, it says there's no gcc or cc so it wont configure. Any help would be appriated.

Thanks,
Mike

---

### Post by Mr_Smiley on 2006-02-14
Hello,

The TinyFugue MUD client can be installed if you have the universe repository enabled. Just open Synaptic and search for 'tf' or type:
```
sudo apt-get install tf
``` into a terminal. 

If you do want to install TinyFugue manually try installing the package 'build-essential' which should contain the packages to let you compile TinyFugue.

Hope this helps :)

---

