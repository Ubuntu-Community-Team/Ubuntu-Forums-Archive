---
title: "warsow 0.310 is out!"
date: 2007-07-02
forum: Gaming &amp; Leisure
---

### Post by nickless on 2007-07-02
...actually since a few days... how should I update?!

I guess there is no sense in waiting until synaptic updates warsow (if this will happen at all...)
So there is only a tar.gz2 file for an update, with no makefile. Am I supposed to just copy the files in.. well where? I found warsow in /usr/share/games/warsow/ but I don't think thats all :D
I dont want to deinstall and download/install the new version if I don't have to :o
[mirrors to the update and full version]("http://www.warsow.net/forum/viewtopic.php?id=14593&action=new")
a little help would be nice
thx :D

---

### Post by Spalatum on 2007-07-02
I have downloaded the full game but I have no idea how to install it. Can someone please help me out?

---

### Post by FoolsGold_MKII on 2007-07-02
Pretty simple.

First, uninstall Warsow from Synaptic - the repos are quite out of date with many games which have had updates.

Second, download the full game from the link nickless gave (the filename you should look for is **warsow_0.31_linux.tar.gz**)

Third, in the command line change directory to where you downloaded the game and run

tar -zxf warsow_0.31_linux.tar.gz

cd warsow

./warsow

Pretty simple. Nothing to make, since it's distributed as binaries. Once again, avoid the repos. Nexuiz and Xmoto are also out of date if you get them from the repos.

I'd recommend you don't try to download and unpack the update over the synaptic version. Apart from the fact I don't know where it's had its files spread out, the game will have files with different versions mixed around. Much easier just to spend the time downloading the full game (it's only 88MB), unpack it to a folder and run.

---

### Post by nickless on 2007-07-03
Well ok, that sucks, but if there is no other way.... thx :)
In this context I find the repos pretty stupid. Online games have to be up to date or you can't play them online...

---

### Post by Spalatum on 2007-07-03
Can you please explain how do in change the directory in the terminal. I'm still pretty much new to Ubuntu and Linux in general.

---

### Post by FoolsGold_MKII on 2007-07-03
> **Spalatum said:**
> Can you please explain how do in change the directory in the terminal. I'm still pretty much new to Ubuntu and Linux in general.
Sure.

To change directory, you type in a terminal

cd NAME

where NAME is the directory you want to go to. So if you download the warsow package to the desktop (probably the default since you're new), you'd type in

cd Desktop
tar -zxf warsow_0.31_linux.tar.gz
cd warsow
./warsow

Now if you're new to Linux, you can bypass the terminal entirely by finding where you downloaded the package (assuming the desktop), right-clicking the warsow download, selecting "Extract Here", go into the folder it makes and simply double-click the warsow file. Maybe I should have gone that route first, dunno, I have a liking for terminals. :)

---

### Post by Spalatum on 2007-07-05
Thanks a lot. That worked fine. The game runs smoothly and all. But I just want to know how can I make it appear in the Applications>Games>Warsow list? When I installed warsow 0.30 with a deb file it was automatically there.

---

### Post by socomoddjob on 2007-07-07
Or.....

[http://www.getdeb.net/app.php?name=Warsow](http://www.getdeb.net/app.php?name=Warsow)

---

