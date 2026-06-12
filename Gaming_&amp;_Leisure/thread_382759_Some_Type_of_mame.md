---
title: "Some Type of mame?"
date: 2007-03-12
forum: Gaming &amp; Leisure
---

### Post by amantonas on 2007-03-12
Can someone PLEASE give me an instruction on how to get a version of mame for Ubuntu 6.10? I really want it. I have been using mame32 on windows for a long time, and would like something like it.

---

### Post by Sandlst on 2007-03-12
This is how I got my mame setup in dapper.  I think the instructions should work for you though. If you run into trouble just post back.

First follow this: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

Then
```
sudo apt-get install xmame-sdl
```
If using Gnome run the file from here: [http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb]("http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb")

And if using KDE
```
sudo apt-get install kxmame
```

Even if you are using gnome, you might want to try kxmame instead of gxmame, I've heard it is more stable.  After you finish installing run it under (Applications/Games/G(K)xmame) or with ```
gxmame
```or```
kxmame
```
The first time you run it, setup options (like where to look for roms) under the options menu.  I haven't run it in a while, but I remember setting up sound and my joypad was just a case of trial and error with the different options, good luck!  Post back if you have any problems.

---

### Post by amantonas on 2007-03-12
It gave me this error message:


```
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Setting up kxmame (2.0~beta-0ubuntu2~edgy1) ...

Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I typed this In: ```
sudo apt-get install kxmame
```

---

### Post by DoktorSeven on 2007-03-12
I don't think clamav is even a dependency of kxmame; sounds like you have other issues.  

Try a apt-get -f install by itself first.

---

