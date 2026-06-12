---
title: "Freespace 2 - Using fsoinstaller"
date: 2008-09-03
forum: Gaming &amp; Leisure
---

### Post by dfa_geko on 2008-09-03
Anyone have any luck installing this game?  I did a full download/install using this installer and when I run fs2_open, it gives me weird characters...  

I'm trying to follow the instructions on this page: [http://www.hard-light.net/wiki/index.php/FreeSpace_Open_Installer]("http://www.hard-light.net/wiki/index.php/FreeSpace_Open_Installer")

---

### Post by dfa_geko on 2008-09-04
Does anyone know how I can install openal into Ubuntu?

I got FS2 Open installed, I get this:

./fs2_open.bin: 1: ELF: not found
./fs2_open.bin: 1: 1&#65533;: not found
./fs2_open.bin: 1: 8&#65533;: not found
./fs2_open.bin: 1: 8&#65533;&#65533;8&#65533;&#65533;&#65533;P&#65533;&#65533;: not found
./fs2_open.bin: 1: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@@: not found
./fs2_open.bin: 1: cannot open &#65533;&#65533;&#65533;: No such file
./fs2_open.bin: 1: }~&#65533;&#65533;&#65533;jnGu&#65533;&#65533;¹ñØ&#9472;X&#9252;¦&#138;&#152;,: &#9532;&#9146;&#9500; °&#9146;&#9508;&#9532;&#9229;
./°&#9149;2_&#9146;&#9147;&#9226;&#9532;.&#9225;&#9227;&#9532;: 1: É: &#9532;&#9146;&#9500; °&#9146;&#9508;&#9532;&#9229;
./°&#9149;2_&#9146;&#9147;&#9226;&#9532;.&#9225;&#9227;&#9532;: 2: S&#8804;&#9532;&#9500;&#9618;&#9474; &#9226;&#9148;&#9148;&#9146;&#9148;: ")" &#9508;&#9532;&#9226;&#9474;&#9147;&#9226;&#9228;&#9500;&#9226;&#9229;

Any ideas?  I'm thinking I need to install openal, but I went to the [www.openal.org](www.openal.org) and I can't seem to find a linux download. Everything is for Windows or Mac.  Please help!

---

### Post by Perfect Storm on 2008-09-04
OpenAL is in the repository;
```
sudo apt-get install libopenal0a
```


The messy stuff could look like a corrupted file/download.

---

### Post by dfa_geko on 2008-09-04
Hi Everyone,

I have figured it out incase anyone gets this error as well.  Well, it turns out it was my fault.  When I ran the fsoinstaller, there were a bunch of options to select which executables I wanted to install.  By default, Windows, Mac, Linux 32-bit, and Linux 64-bit are selected.  If you run through the installation without reading, it will install everything.  Make sure to select only the executables that you need.  In my case, Linux 32-bit.  

I am thinking what happened is that I also have Linux 64-bit selected. So when it installed, it installed the 64-bit version over the 32-bit. As I executed ./fs2_open, it ran the 64-bit version causing a bunch of garbage on the screen.

Hope this helps anyone who has the same issue.  The main issue really is not reading... :)

---

