---
title: "Cedega and Wine problems"
date: 2005-11-17
forum: Gaming &amp; Leisure
---

### Post by Saku on 2005-11-17
Okay, call me crazy but.. For the last 24 hours, I've been sitting here trying to get either Cedega CVS or Wine CVS with Winetools installed.

I seem to fail misserably and I yet don't know what it is I am doing wrong.

Basically, I want either installed so I can get to play this one game.
(Wether it matters or not, the game is Ragnarok Online and F.E.A.R.)

I've followed these two tutorials down to the smallest detail under installing and god knows what.

the packages are present and installed on my Ubuntu Breeze 5.10 System but somehow, they seem to fail along the lines.


[The Wine tutorial I followed.](http://www.ubuntuforums.org/showthread.php?p=149181)

[The Cedega tutorial I followed.]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45")

The errors I came across with the Wine tutorial was:
**wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory**
I tried reading up on it on the Wine wiki and on google, but it didn't seem to help me fix the problem.

On Cedega however, I failed under the process of making it. (Right after compiling) Error in the makefile maybe?  I don't know.


Does anybody have any solutions or .. know how I can fix either of these problems?  Anything would help.

Thanks in advance.
 --Saku.

---

### Post by YokoZar on 2005-11-17
Try using the Wine binary packages from winehq.org

That howto is a bit weird.

Now that the latest winetools is out, I suppose I should package it up as well ;)

---

### Post by Saku on 2005-11-17
Alrighty.  I'll try with the new binary package from winehq.org and check if it's any better.  :P

If not I'll be replying here shortly. (It's 4:48.A.M. so if not around 5-6am, later today.)

Edit:

I installed the new Wine through winehq.org and installed winetools with it.
Created a fake windows drive in ~/.wine and was going to install DCOM98.

The concole gave me these errors under the install;
```

grep: /home/saku/.wine/installed.reg: No such file or directory
grep: /home/saku/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/saku/.wine/installed.reg': No such file or directory
software installation verified by /home/saku/.wine/winetools.log
ls: dcom98.exe: No such file or directory

downloading http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE to dcom98.exe with 1229056 bytes...
WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
waiting for wineservers to exit...

```

While the setup of DCOM98 after iniciating the exe gave me this error;

```

DCOM98 can only be installed on Windows 98.
For Windows NT, please install the latest service packs.

```
Even though, Winetools registers DCOM98 as installed.  Anything wrong here? (Or should it be this way.)

Furthermore, let's try to install Internet Explorer 6.0 SP1.
This little thing gives me an error message saying that it failed to connect to the internet to download the missing components, even though it connected to the internet to "download" the ie60.exe setup.
The installation fails and the terminal is filled with lots of errors and grep failures, failing at exporting a registry key because as simple as it is, it doesn't exist!

Anything would help me here.. Really.

In advance, thanks.

---

### Post by cluelessnoob on 2005-11-18
I wouldn't worry about winetools... are they outdated in .09.1?

Is it showing as installed in synaptic and do you have a ~/.wine/drive_c 
directory?

If so I think wine is installed.

I used wineconfig and had to "wine regedit" that drive_c directory to point to my D: drive but now my games work.

---

### Post by Mies on 2005-11-29
I had problems with make for cedega as well untill I read [this]("http://ubuntuforums.org/showthread.php?t=71099&page=2") thread. Basically when you use GCC3.4 there are no problems.

Mies

---

