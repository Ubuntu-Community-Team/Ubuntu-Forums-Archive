---
title: "Help: How to run Gparted ap?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by intelliprompt on 2006-09-28
I was told in another thread that I needed to run the Gparted ap to format my HD. I couldnt find it and so I ran a search. Upon finding and trying to run it, I was given the following error:

Root privileges are required for running GParted
Since GParted can be a weapon of mass destruction only root may run it.

I need help with this because I would like to put Linux on my new HD so I can expand my media storage HD. Also, all of the above was done with the live CD. I'd also like to know if running GParted would make my HD unusable to windows for storage, as I am so new to Linux, I still use Windows XP for most things and want to be able to have my music able to run on both OSs. Any and all input and help is appreciated. Thanks.

---

### Post by katalyst23 on 2006-09-28
I am a bit confused about your setup and what you are trying to do.  Which hard drive are you putting Linux on, and where is Windows right now?

As for sharing files between Windows and Linux, if you create a FAT32 partition, both OSes can read and write to that filesystem.

---

### Post by andypaxo on 2006-09-28
If you run GParted from the applications menu, it should ask for your password.
If you want to run it from the command line, type 'sudo gparted' and then enter your password.

GParted *is* a weapon of mass destruction, though... make sure you know what you are doing before using it!

---

### Post by intelliprompt on 2006-09-28
Windows XP and all apps are on a 40Gb drive, and Linux and my music is currently on a very very cramped 30Gb drive. I want to put Linux and my music on a new 160Gb drive. The 160Gb drive is the one I'm trying to format and partition and install Linux onto. The big drive is also the one I was concerned about Windows XP not being able to read if I use Gparted.

---

### Post by andypaxo on 2006-09-28
Okay, if you're just formatting a brand new disk, there's not too much potential for destruction.

As katalyst23 says, if you want to share data between Windows and Linux, it would be best to put your data on a FAT32 partition.
It's not the best format around, and there are ways to share other formats - but you will have a much, much easier time with FAT32

---

### Post by intelliprompt on 2006-09-28
Thank you very much! It took a little bit for me to figure out what I was doing, but I got everything set up and running fine. All thats left for me to do now is transfer my music and configure Linux and transfer or figure out how to share files between OSs! Heh... another day. Thanks again for your patience with such a beginner.

---

