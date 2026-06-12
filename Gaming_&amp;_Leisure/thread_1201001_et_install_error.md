---
title: "et install error"
date: 2009-06-30
forum: Gaming &amp; Leisure
---

### Post by accLinux on 2009-06-30
While trying to install enemy territory, I get:



nick@nick-desktop:~$ cd ~/Desktop
nick@nick-desktop:~/Desktop$ chmod +x et-linux-2.55.x86.run
nick@nick-desktop:~/Desktop$ sudo ./et-linux-2.55.x86.run
[sudo] password for nick: 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/nick/.setup7312: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting


Seems like I need another lib.?

---

### Post by beastrace91 on 2009-07-01
A quick google search yielded me [this thread](http://ubuntuforums.org/showthread.php?t=229457)

Hope it helps,
~Jeff

---

### Post by accLinux on 2009-07-01
> **beastrace91 said:**
> A quick google search yielded me [this thread](http://ubuntuforums.org/showthread.php?t=229457)

Hope it helps,
~Jeff

Still get the same error message. I'm using Ubuntu 9.04, 32 bit. I've actually had quite a few lib. problems with ubuntu games: alien arena, urban terror, and now et. Did they remove some of the libs that came with ubuntu 8.10?

---

### Post by Coalinn on 2009-07-01
I had trouble installing et the other day.  How are you going about the install?  I first tried fileshack, then going from there.  However I had similar problems with libraries.  I then deleted any et file and tried: 

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

and using:
```
wget -c http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run
```once I installed the file (this method takes significantly more time than a file-sharing website) I entered in the terminal:

```
sudo sh ./et-linux-2.60.x86.run
```And everything worked for me, hopefully this works for you too.

---

### Post by accLinux on 2009-07-02
> **Coalinn said:**
> I had trouble installing et the other day.  How are you going about the install?  I first tried fileshack, then going from there.  However I had similar problems with libraries.  I then deleted any et file and tried: 

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

and using:
```
wget -c http://ftp.games.skynet.be/pub/wolfenstein/et-linux-2.60.x86.run
```once I installed the file (this method takes significantly more time than a file-sharing website) I entered in the terminal:

```
sudo sh ./et-linux-2.60.x86.run
```And everything worked for me, hopefully this works for you too.

Installed ET! Thanks

---

