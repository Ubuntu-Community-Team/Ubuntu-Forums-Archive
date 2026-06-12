---
title: "Cant Find Fluxbox in apt-get"
date: 2005-11-13
forum: Desktop Environments
---

### Post by deceasedcomrade on 2005-11-13
I read somewhere that all i needed to do to get fluxbox working was "sudo apt-get install fluxbox" and i was amazed (this is my first time really using package managers) and so when i went to do it all i got back was a couldnt find package error... what do i have to do to get my new ubuntu install to find packages, or what do i do to find packages properly? also do i need to do anything else to get fluxbox working once its installed? 
thanks!

---

### Post by manicka on 2005-11-13
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by manicka on 2005-11-13
I'd install openbox, openbox-themes and obconf

---

### Post by manis on 2005-11-14
Hi,
I install Fluxbox by download it from fluxbox website. Try to search at yahoo or gogle their address. You must complile this file and for me everthing is ok.
thank you.

---

### Post by Xian on 2005-11-26
[QUOTE=manis]Hi,
I install Fluxbox by download it from fluxbox website. Try to search at yahoo or gogle their address. You must complile this file and for me everthing is ok.
[/QUOTE]

Fluxbox is a part of the Universe repos.
Just enable them and there is no need to compile it from source.

```
$ apt-cache policy fluxbox
fluxbox:
  Installed: 0.9.12-1build1
  Candidate: 0.9.12-1build1
  Version table:
 *** 0.9.12-1build1 0
        500 http://archive.ubuntu.com breezy/universe Packages
        100 /var/lib/dpkg/status
```

---

### Post by erik-the-red on 2005-11-26
It's actually not that hard to compile fluxbox from source; I recommend it wholeheartedly.

I remember the Hoary Fluxbox binary was *terrible*. It took about half a minute to load up. My compiled one takes five seconds.

---

### Post by Xian on 2005-11-26
[QUOTE=erik-the-red]I remember the Hoary Fluxbox binary was *terrible*. It took about half a minute to load up. My compiled one takes five seconds.[/QUOTE]
Yeah, the one in Hoary did pretty much blow. It was fixed in Breezy and now loads promptly. I can notice no difference between the compiled version I made and the binary installation.

---

### Post by sanguinemoon on 2005-11-26
I was able to get Fluxbox just from Synaptic ;)

---

