---
title: "Can't download Screenlets"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by maduranga on 2007-07-22
**Hello.... I'm trying to download and install Screenlets after adding "deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets" to my surces list and by giving the command "sudo apt-get install screenlets" but at the middle of the instalation process, it gives the following error message.**

[I]Get:1 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets screenlets-extra 0.0.7-17 [1396kB]
Err [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets screenlets-extra 0.0.7-17
Error reading from server. Remote end closed connection
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/pool/feisty/screenlets/screenlets-extr](http://hendrik.kaju.pri.ee/ubuntu/pool/feisty/screenlets/screenlets-extr)... Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/I]

**Can someone help me to overcome this problem and get the Screenlets installed?**  :(

---

### Post by pjones0404 on 2007-07-22
after adding the repo to your sources.list did you run sudo apt-get update?

i would do this and then try to install it again.

---

### Post by LuisAugusto on 2007-07-22
Screenlets severs sucks.
For some reason the connection close after some time, run the:

```
sudo apt-get install screenlets
``` from the terminal until it finish the download

Pitful, I know, but it's the only way xD

---

### Post by Deco_21 on 2007-07-22
u need the screenlets key.

```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add - && sudo apt-get update


```

But right now Screenlets its very unstable. In fact you can use screenlets who have internet connection. For some strange reason everything crash.

---

### Post by Jhongy on 2007-07-23
the screenlets repo is aon a server that appears to be blocked / censored in China.

If anyone could put up a mirror repo for us people affected by this, it owuld be much appreciated.

---

### Post by maduranga on 2007-07-23
thx i got it working. i had to give that command several times until screenlets is fully downloaded and installed. but now i got it installed. thx alot

---

