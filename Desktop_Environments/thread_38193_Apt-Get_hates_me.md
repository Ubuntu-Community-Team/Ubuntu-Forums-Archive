---
title: "Apt-Get hates me"
date: 2005-05-30
forum: Desktop Environments
---

### Post by Pitbull11188 on 2005-05-30
When I attempt to use sudo apt-get update and sudo apt-get upgrade, they don't work. They worked fien up until about a week ago. When I eneter these two commands in the shell i get this response:

Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release.gpg
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Connection failed
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg
  Connection failed
25% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting


Help me please!

---

### Post by thagame on 2005-05-30
looks to me like its not your pc but the repository site isnt connecting.

---

### Post by bored2k on 2005-05-30
[QUOTE=thagame]looks to me like its not your pc but the repository site isnt connecting.[/QUOTE]
 Try changing your repositories
```
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

And by the way, backports main is now forbidden, so you need a mirror like the one I have.

---

### Post by Pitbull11188 on 2005-05-30
Thats what I think to but I don't know what to do to fix it. I keep getiing the gui of the urgent upf=dates popping up in my taskbar but even when i try to use the gui it doesn't work and neither does apt-get so I don't know what to do. Anyone else had these problems? If so, How'd you dfix it?

---

### Post by bored2k on 2005-05-30
[QUOTE=Pitbull11188]Thats what I think to but I don't know what to do to fix it. I keep getiing the gui of the urgent upf=dates popping up in my taskbar but even when i try to use the gui it doesn't work and neither does apt-get so I don't know what to do. Anyone else had these problems? If so, How'd you dfix it?[/QUOTE]
 Did you replace your repository list with the ones pasted ? Do this with
```
sudo gedit /etc/sources/list && sudo apt-get update
```

---

### Post by Pitbull11188 on 2005-05-30
It's still giving me trouble. I think I may have messed up my sources.list file. Here is what it reads:


deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview amd64 Binary-1 (20050330)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Thanks.

---

### Post by Pitbull11188 on 2005-05-30
Could someone with a working 64-bit sources.list file possibly post it here so that I could use it?

---

