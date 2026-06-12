---
title: "new to ubuntu....maybe a simple question.."
date: 2006-04-23
forum: Desktop Environments
---

### Post by nccman19 on 2006-04-23
I'm new to Ubuntu and Linux in general...I have absolutely no idea how to install any programs that I've downloaded...It's probably easy but I have no clue how to do it...If anyone could help me out that'd be awesome

---

### Post by verde on 2006-04-23
Hi and welcome to Ubuntu :)
I suggest you to install new applications using the program in "Applications -> Add/Remove Applications" (i'm using Gnome in italian, I hope my translation is right). For installing new application you need to insert your password.

---

### Post by nccman19 on 2006-04-23
The programs I was referring to are like Yahoo Messenger, Media Players and things like that.  Programs I had in Windows.  Some tips I've found say something about .deb and .rpm but I've tried those and it doesnt work.  Some of the files I've downloaded are .bin and .tgz.

---

### Post by kh4nh on 2006-04-23
[QUOTE=nccman19]The programs I was referring to are like Yahoo Messenger, Media Players and things like that.  Programs I had in Windows.  Some tips I've found say something about .deb and .rpm but I've tried those and it doesnt work.  Some of the files I've downloaded are .bin and .tgz.[/QUOTE]

You can use Gaim instead to connect to your Yahoo account. If you really wanna use Yahoo go here. The install instruction is on the right side [http://messenger.yahoo.com/unix.php;_ylt=AiuKTt1Um0jeBBYp2xK1K6BwMMIF]("http://messenger.yahoo.com/unix.php;_ylt=AiuKTt1Um0jeBBYp2xK1K6BwMMIF")

is Media Players you referring to Windows Media Player, if it is, there is no such thing. You could use Mplayer or Xine instead.

Windows's equivalent software in Linux: [http://www.linuxrsp.ru/win-lin-soft/table-eng.html]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")

[https://wiki.ubuntu.com/WhatWindowsUsersWant]("https://wiki.ubuntu.com/WhatWindowsUsersWant")

---

### Post by verde on 2006-04-23
[QUOTE=nccman19]The programs I was referring to are like Yahoo Messenger[/QUOTE]
For Yahoo Messenger try **Gaim** (Applications -> Internet -> Gaim)

[QUOTE=nccman19]Media Players and things like that.  Programs I had in Windows. [/QUOTE]
You can use **Totem** (Applications -> Audio & Video), but you need to install the correct CODEC. For other stuff (include the CODEC) install **Automatix** [http://www.ubuntuforums.org/showthread.php?t=138405]("http://www.ubuntuforums.org/showthread.php?t=138405")

[QUOTE=nccman19]Some tips I've found say something about .deb and .rpm but I've tried those and it doesnt work.  Some of the files I've downloaded are .bin and .tgz.[/QUOTE]

If you have a .deb file you need to open a terminal, go to the directory that contains your brand-new file, and type
```
sudo dpkg -i brand-new_file.deb
```

A .tgz (or .tar.gz or tar.bz2) is like a .zip file, that is an archive, so extract it and read the **README** file into the new directory.

.bin are just linux executable files, with Gnome you need only to double-click them (I think).

---

### Post by nccman19 on 2006-04-23
I'm getting how to use the terminal to install the .deb files.  But the problem I'm running into now is something with dependancies.  Any idea?

---

### Post by danish_demon on 2006-04-23
try this (from the terminal):

```
sudo apt-get install build-essentials
```

---

### Post by kh4nh on 2006-04-23
[QUOTE=nccman19]I'm getting how to use the terminal to install the .deb files.  But the problem I'm running into now is something with dependancies.  Any idea?[/QUOTE]
can you be a little more specific. What are you trying to install, what dependencies error is that,

---

