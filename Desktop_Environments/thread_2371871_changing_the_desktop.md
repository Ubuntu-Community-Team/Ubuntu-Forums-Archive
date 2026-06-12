---
title: "changing the desktop"
date: 2017-09-19
forum: Desktop Environments
---

### Post by bricro on 2017-09-19
I would like to now if someone can explain to me how to get the desktop from easypeasy ubuntu onto lubuntu or other ubuntu flavour. I would just update easypeasy but apparently it's not possible or not easy. However i like the desktop and was going to install some light variant of ubuntu and hopefully install the easypeasy desktop. I am not very linux savvy so if it's possible to install the desktop can you provide detailed instructions please. Thanks in advance Brian.

---

### Post by vasa1 on 2017-09-19
According to [http://distrowatch.com/table.php?distribution=EasyPeasy](http://distrowatch.com/table.php?distribution=EasyPeasy) easypeasy is discontinued. I suggest you stay away from it.

---

### Post by TheFu on 2017-09-19
For supported flavors of Ubuntu, you can load many different desktops and pick which one is used just prior to login.
If the desktops are based on similar libraries, it is possible for them to save conflicting settings, so while I'm checking out different desktops, I'm always using a new user account. This way, the HOME is different and all the settings are put where I don't care.  After each different desktop environment is tested, I wipe the HOME for that new user account, pick a different DE and login to try the next one.

Ok ... so none of this helps with a DE that doesn't follow the rules.  I know **ZERO** about the DE you mention.  Also, different distros will have different core libraries, so mixing and matching different DEs might not be possible.  It might work, but it might be unstable.  Just depends on how tightly coupled the DE is with the underlying OS.

Also, I suspect that DE hasn't been maintained correctly over the years. It is a security nightmare just waiting to happen.  Please take a look at 16.04 xubuntu or lubuntu as alternates.  These both have support until April 2019. That means someone is making security patches and updates for the core packages.  I looks like the last EasyPeasy release was based off 12.04 - ouch. No support.  You may know know this, but that is as dangerous as running WinXP.  There are many, many, remote root access modes on 12.04. Be afraid if you ever take that machine to a public network, cafe, hotel, library.  Be very afraid.

You can make Lubuntu look like easy peasy with icons on the left. I did this for my mother with Lubuntu 10.04. Took about 15 min of effort.

Before heading off to try any of this stuff, be certain you have a know-you-can-restore backup.  It could end with a system you cannot log into.  If that scares you, please, please, please make a backup that you can restore first AND backup any really critical data separately.

I want to scare you into 2 things:
* Get on a supported LTS.
* Get a backup.

---

### Post by Frogs Hair on 2017-09-19
There hasn't been a new release of easypeasy since 2010 which is a Gnome 2 release and not likely to work with current versions of Ubuntu. I see no PPA for this desktop either.

---

### Post by bricro on 2017-09-21
thanks for the info folks. I understand the outdated easypeasy issues which is why i was asking about using the DE on a newer ubuntu distro. I will now leave that idea alone and just accept the change of a new install. Thanks again.

---

