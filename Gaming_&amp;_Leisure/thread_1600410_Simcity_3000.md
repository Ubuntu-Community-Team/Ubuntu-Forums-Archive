---
title: "Simcity 3000"
date: 2010-10-18
forum: Gaming &amp; Leisure
---

### Post by issachan on 2010-10-18
Hi all, 

I am trying to install Simcity 3000 (demo version) on Ubuntu 10.04. I wanted to try the demo out as I managed to track down a copy of the full version. I'd like to figure out how to get it working.

I managed to download files sc3u-demo-x86.run but it won't run. I've tried using chmod +x and ./ to run it, tried it with sudo as well, but nothing has worked so far.

I've tried the Lokigames demo installer located here: [http://www.lokigames.com/products/demos.php3](http://www.lokigames.com/products/demos.php3) and tried to same commands as I did with the other file, but no luck.

I did a few searches and came across some forum posts and several web pages, but I haven't much experience in installing these sorts of programs and I think a lot of the information is out of date and does not apply to this version of Ubuntu. 

Please help!

Thanks in advance!
[I]
* FYI - the version of Simcity 3000 I'm trying to install is the linux version for both the demo and the full version.[/I]

---

### Post by Ctrl-Alt-F1 on 2010-10-19
Can you say exactly what the error message is?  I run a 64bit system, and almost every time I can't run a game, it's because it requires 32bit libraries.

If that's the case:
apt-get install ia32-libs

---

### Post by issachan on 2010-10-19
> **Ctrl-Alt-F1 said:**
> Can you say exactly what the error message is?  I run a 64bit system, and almost every time I can't run a game, it's because it requires 32bit libraries.

If that's the case:
apt-get install ia32-libs

Here's the error I got when I ran *sudo sh sc3u-demo-x86.run*

Creating directory sc3u_demo
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 1927418100 841450463

Any idea what it means?
[LEFT] 
    

[/LEFT]

---

### Post by Ctrl-Alt-F1 on 2010-10-20
If there is an error in the checksums it means the file that is corrupted (i.e. the file that exists on your computer is not the same as what the installer is expecting).  You could try re-downloading.  I don't know enough about the game to tell you much more than that.

---

### Post by rettichschnidi on 2010-10-20
a) "export _POSIX2_VERSION=199209" should help
b) I sent you a PM, try that.

---

