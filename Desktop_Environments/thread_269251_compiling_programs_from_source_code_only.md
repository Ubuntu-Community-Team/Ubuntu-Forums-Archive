---
title: "compiling programs from source code only"
date: 2006-10-01
forum: Desktop Environments
---

### Post by wigglezZA on 2006-10-01
Hi, I'm a very new ubuntu/linux user and don't know much about it. The problem i have is that i don't have an internet connection on my PC so i can't use reposistories to install new programs. I have acces to an internet connection though and i can download the source codes of the programs i want to install (e.g xmms, gnomebaker, vlc, mplayer). Can someone please explain to me how to compile and configure programs from source code only. some of them also have other plugins you must install with them, could you please also explain how to do this.

---

### Post by croak77 on 2006-10-01
You might want to just download the .deb's instead of the source code. If you go to [http://packages.ubuntu.com](http://packages.ubuntu.com) , you can search for a program you want, it will list all needed dependencies (they will have a red dot next to them), and then you can download by selecting your architecture.

---

### Post by wigglezZA on 2006-10-02
After i've downloaded the .deb's how do i install them?

---

### Post by marufsiddiqui on 2006-10-02
Just double click on the .deb file & it willopen with package manager, there's a option "Install", if u see "All dependencied funfilled" then click it -->then it would ask for root permission, grant it & it will install

for some cases u may see the red error messg "dependency not satisfied" & showing the necessary package for that program.

again for some other cases, u may see u need to download additional packages.

i had the same problem plz [see]("http://ubuntuforums.org/showthread.php?t=261990")

---

### Post by taurus on 2006-10-02
From a terminal, type

```
sudo dpkg -i <filename>.deb
```

---

### Post by dannyboy79 on 2006-10-02
i ahve a much better solution. i have read somewhere that you can actually download everything from the repositories and you would setup your sources.list so that it read from the cd everytime you wanted to install something, here is the link to download iso images of its main, universe and multiverse repositories. they are .torrent files. 

[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

once you download the 3 dvd's and the cd, you can use the cd's as your apt-get.

---

