---
title: "Tremulous isn't free (as in freedom) software?"
date: 2007-01-02
forum: Gaming &amp; Leisure
---

### Post by guyjohnston on 2007-01-02
Does anyone know why the game Tremulous is in the Muliverse repository rather than Universe? From what I can tell from the 'Copyright' files, the code is under the GNU GPL except for a few exceptions under other compatible free licences such as the Zlib licence, and the 'media' is under the Creative Commons Attribution-ShareAlike Licence, which I'd have thought also counts as a free licence.

---

### Post by Sammi on 2007-01-03
I believe it even uses the gpl'd quake 3 engine.

Check out the wikipedia.org article:
[http://en.wikipedia.org/wiki/Tremulous](http://en.wikipedia.org/wiki/Tremulous)

Maybe this is something worth metioning to the Ubuntu repository MOTUs. See this page for MOTU contact info: [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by compiledkernel on 2007-01-03
I believe it lives in multiverse because its a community provided package, but I could be wrong.

---

### Post by rajeev1204 on 2007-01-04
hi

Tremulous is in repository?? where? FOr dapper 64 bit?

---

### Post by Sammi on 2007-01-04
Searching on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) gave me these results under dapper backports:
 > **Package Search Results**

 You have searched for packages that names contain *tremulous* in distribution *edgy*, all sections, and all architectures.


Found *4* matching packages, displaying packages 1 to 4.
**Package tremulous**[LIST]
[*][edgy]("http://packages.ubuntu.com/edgy/games/tremulous") (games): Aliens vs Humans, team based FPS game with elements of an RTS   [[COLOR=red]multiverse[/COLOR]] 
1.1.0-2: amd64 i386 powerpc[/LIST]**Package tremulous-data**[LIST]
[*][edgy]("http://packages.ubuntu.com/edgy/games/tremulous-data") (games): Tremulous datas   [[COLOR=red]multiverse[/COLOR]] 
1.1.0-1: all[/LIST]**Package tremulous-doc**[LIST]
[*][edgy]("http://packages.ubuntu.com/edgy/games/tremulous-doc") (games): Tremulous documentation   [[COLOR=red]multiverse[/COLOR]] 
1.1.0-2: all[/LIST]**Package tremulous-server**[LIST]
[*][edgy]("http://packages.ubuntu.com/edgy/games/tremulous-server") (games): Tremulous server   [[COLOR=red]multiverse[/COLOR]] 
1.1.0-2: amd64 i386 powerpc[/LIST]

I'm not 100% sure about this, but I think you can just add these lines to your /etc/apt/sources.list file and it should show up in Synaptic:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

You edit sources.list by doing this command:
> gksudo gedit /etc/apt/sources.list

---

### Post by darkazurka on 2009-11-13
You know one of the top maps ATCS? It contains media that is non-free culture.

So, in your maps folder that came with your game: (if you installed it through synaptic or apt-get , then it can be found at 
```
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3
```

You can open it with for example "Archive Manager" and inside you find the file ```
atcs.txt
```

There under [ other notices ] you find   ```
textures by yves allaire fall under this license:

   http://creativecommons.org/licenses/by-nd-nc/1.0/
```

Also textures from shaderlab: > Other non-commercial applications are considered on a case-by-case basis via e-mail.
which is the only mention of commercial rights, meaning that it probably falls under a similar license to cc-by-nc-sa , so you are not allowed to use it for commercial purposes.

So the stated media being under CC-BY-SA 2.5 is false. I guess they didn't think it priority one to make it clear WHAT is licensed under WHICH license.

A quick look. The popular map Niveus also has textures from yves allair:    > textures by yves allaire fall under this license:

   [http://creativecommons.org/licenses/by-nd-nc/1.0/](http://creativecommons.org/licenses/by-nd-nc/1.0/)
Quick link if you've installed Tremulous from Synaptic or apt-get or any other package manager: ```
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3
``` (open map-niveus-1.1.0.pk3) and inside you find the file ```
niveus.txt
```

This can help also as a reference on why Tremulous is in Multiverse

---

