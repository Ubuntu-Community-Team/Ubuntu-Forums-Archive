---
title: "Can't install steam"
date: 2013-02-13
forum: Gaming &amp; Leisure
---

### Post by lFuidy on 2013-02-13
I know by this point installing steam on ubuntu should be relatively straightforward, but I'm having this issue which has never happened before.
So I download the steam_latest.deb file, fire up the terminal, type in the commands:
```
cd Downloads
sudo dpkg -i steam_latest.deb
```
What I get is:
```
(Reading database ... 207918 files and directories currently installed.)
Unpacking steam (from steam_latest.deb) ...
dpkg-deb (subprocess): cannot copy archive member from 'steam_latest.deb' to decompressor pipe: unexpected end of file or stream
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing steam_latest.deb (--install):
 cannot copy extracted data for './usr/lib/steam/bootstraplinux_ubuntu12_32.tar.xz' to '/usr/lib/steam/bootstraplinux_ubuntu12_32.tar.xz.dpkg-new': unexpected end of file or stream
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 steam_latest.deb
```
So I proceed with:
```
sudo apt-get -f install
```
This usually solves the problem and installs steam but this time I just get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```
I'm a Linux newbie so pardon if the answer might be dead simple. I am using Ubuntu 12.10 64-bit.
Also, If I try double-clicking on the .deb file so it would install steam through the software center, I get this:
[IMG]http://i512.photobucket.com/albums/t327/Ghosteyya/Screenshot_zps98b14e6f.png[/IMG]

---

### Post by fdrake on 2013-02-13
are you sure the file is not corrupted . Can you install from the repo?
do not know the steam package but try this:
```
sudo apt-get install aptitude
sudo aptitude search steam  
<look the valve package's name and copy it>
sudo apt-get install <steam package name>
```

or if you are lucky , you can jsut try ```
sudo apt-get install steam
```

---

### Post by JoshuaMiller0 on 2013-02-13
I simply openned the .deb with ubuntu software centre, hit install and then openned the downloader/ installer it made and half an hour later I had steam open.

---

### Post by lFuidy on 2013-02-13
> **fdrake said:**
> ```
sudo aptitude search steam
```

Nothing happens after this. Literally no feedback code displayed.

---

### Post by mentorious on 2013-02-13
The file is corrupted for 99,9%.

 Get the package again, try with wget, you'll be sure that isn't error during downloading :)

```
wget http://media.steampowered.com/client/installer/steam.deb
```

and then without USC
```
sudo dpkg -i steam.deb
```

---

### Post by lFuidy on 2013-02-13
> **mentorious said:**
> The file is corrupted for 99,9%.

 Get the package again, try with wget, you'll be sure that isn't error during downloading :)

```
wget http://media.steampowered.com/client/installer/steam.deb
```

and then without USC
```
sudo dpkg -i steam.deb
```

Thank you, that finally worked. Although I had to add 
```
sudo apt-get -f install
``` in the end but thanks. :)

---

