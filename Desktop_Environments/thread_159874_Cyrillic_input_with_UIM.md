---
title: "Cyrillic input with UIM"
date: 2006-04-13
forum: Desktop Environments
---

### Post by jimw on 2006-04-13
I've just tried to work scm, and it ends up wiwth a Segmentation fault.

I'm not sure, but it seems that this seg  fault is not going to be fixed for Dapper, so I went to UIM.

Got it all apt-got and installed, but can't find the "starting handle"

Anyone give me some tips on how to input the Kazakh language through it?

(I've got the m17n db on my drive, which includes kazakh)

Thanks

---

### Post by stuporglue on 2006-04-13
> I'm not sure, but it seems that this seg fault is not going to be fixed for Dapper, so I went to UIM.

I'm sorry I can't help with the input. Did you file a bug, or find one already filed for this issue? If there isn't one, and you file a bugreport, maybe it will be fixed.

---

### Post by Sef on 2006-04-13
First make sure that universe is open.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")


Then go to this site and follow the follow the directions.   There is a lot to download, so if you have any questions, please ask.

[http://packages.ubuntulinux.org/dapper/misc/console-cyrillic]("http://packages.ubuntulinux.org/dapper/misc/console-cyrillic")

---

### Post by jimw on 2006-04-13
[QUOTE=Sef]First make sure that universe is open.

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")


Then go to this site and follow the follow the directions.   There is a lot to download, so if you have any questions, please ask.

[http://packages.ubuntulinux.org/dapper/misc/console-cyrillic]("http://packages.ubuntulinux.org/dapper/misc/console-cyrillic")[/QUOTE]

As I understand it, this would change my computer over to entirely Cyrillic, be it Kazakh, Belarussian, or whatever.  

I do most of my work in English, and only want to be able to input pieces in Kazakh.

Thanks for the suggestion, though.

JimW

---

### Post by jimw on 2006-04-18
Don't have uim working, but our local Ubuntu guru came over tonight to help get my printer working properly for me.

After we'd done that, we fooled around with the Kazakh problem.

After a bit of going here and there, we got the xkeyboard-config_0.8-6_all.deb file downloaded from Dapper.  The whole thing would have been easier if it weren't for dependencies that made it impossible to just install this whole thing.

However, we were able to extract the 'kz' file, and slip it into /etc/X11/xkb/symbols.  However, the 'keyboard layouts' file wasn't able to find it.  So we took 'mn' (Mongolian) and labelled it mn-old, and labelled the kazakh as 'mn'.

And it works.

&#1082;&#1257;&#1088;&#1110;&#1089;&#1082;&#1077;&#1085;&#1096;&#1077;!
Jim W:)

---

