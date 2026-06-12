---
title: "Darwinia demo, Ubuntu edgy eft x64, libgtk"
date: 2007-04-09
forum: Gaming &amp; Leisure
---

### Post by Capslock118 on 2007-04-09
Hello,
I purchased defcon awhile back and it was a wonderful game. Thank you. Now I have went to try darwinia. I run Ubuntu edgy eft x64 edition and have tried to install the demo but get this error:

```

joel@joel-desktop:/media/games/Darwinia-Linux$ sudo sh darwinia-demo2-1.3.0.sh
Verifying archive integrity... All good.
Uncompressing Darwinia demo2 1.3.0.......................................................................
/home/joel/.setup29116: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
joel@joel-desktop:/media/games/Darwinia-Linux$

```


I searched this entire forum and beyond and have found others with similar problems but all I have found was people saying install libgtk-1.2 or others just plain quit trying

well......

```

joel@joel-desktop:/media/games/Darwinia-Linux$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joel@joel-desktop:/media/games/Darwinia-Linux$

```


so what is my solution? I cant seem to find an answer....

I did find someone suggestion moving a libgtk file to lib32 folder but I am unsure where i would start with that.

Thanks for any help guys

---

### Post by Capslock118 on 2007-04-10
bump :-/

---

### Post by Capslock118 on 2007-04-11
final bump

so i guess no one knows of an answer?

---

### Post by FoolsGold on 2007-04-11
Two suggestions before you give up:

(1) Download the demo again (probably won't help, says integrity is good, but worth a shot anyway)

(2) Do not use 64-bit Linux!

When I was trying to get Quake 4 to work on 64-bit Ubundu Dapper a while back, it wouldn't work. Complained about libSDL not being there, when I could clearly see it was. It even had that "cannot open shared object file: No such file or directory" referencing a library that DID exist! I hunted down and found out that Quake 4 would only understand the 32-bit version of SDL, so I swapped out libraries with the 32-bit versions, and it ran just fine. Maybe the Darwinia installer doesn't understand the 64-bit GTK libs.

---

### Post by Capslock118 on 2007-04-11
Thank you FoolsGold for replying.
  The first suggestion I have tried many a times.

As for the second well. First I dont have time to worry about moving to 32bit and most importantly. I have been able to run EVERYTHING else given enough time to set up. Some things have been interesting but aside from darwinia, everything runs great.

You did imply about the lib32 stuff and all i have to say is. I have a lib32 and lib64 are in my fs. I remember having to do this in order to get wine to work. So, i have 32-bit emulation running on my machine i think?...nearly positive..though what i really mean may not be the word emulation.

so I guess what I am looking at here is finding a way to get the libgtk into the lib32 area without affecting the rest of my system....does this make sense?

---

### Post by FoolsGold on 2007-04-12
> **Capslock118 said:**
> so I guess what I am looking at here is finding a way to get the libgtk into the lib32 area without affecting the rest of my system....does this make sense?
It does, sorta. It's like when people run the 32-bit version of Firefox so they can use Flash, which won't work in 64-bit as I understand it.

Don't know how to help you there, someone else might, or you could keep googling.

---

