---
title: "How to install mplayer?"
date: 2006-01-14
forum: General Help
---

### Post by bombfans on 2006-01-14
I used the totem, but it do not work on rmvb format. So, I want to know how to install mplayer?

Thanks!

---

### Post by stoffepojken on 2006-01-14
[http://www.ubuntuforums.org/showthread.php?t=85190]("http://www.ubuntuforums.org/showthread.php?t=85190")

---

### Post by learning curve on 2006-01-14
wget [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb)
sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb

Copy and paste the above command in Terminal.  This program is called Automatix and will install many programs on your system that you choose to install including Mplayer and the Mplayer plugin for Firefox.  After you install automatix you can launch it from Applications/System tools.

Hope this helps you out.
Learning curve

---

### Post by angrykeyboarder on 2006-01-14
Or if these answers seem like a bit much, there's alwyas...

sudo apt-get install mplayer

---

### Post by Sureshot324 on 2006-01-14
[QUOTE=angrykeyboarder]Or if these answers seem like a bit much, there's alwyas...

sudo apt-get install mplayer[/QUOTE]

Yeah that's the best way.  I believe you have to uncomment all the extra sources in /etc/apt/sources.list for that to work though.

---

