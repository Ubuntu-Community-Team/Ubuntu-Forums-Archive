---
title: "Tar.gz file"
date: 2009-01-31
forum: Desktop Environments
---

### Post by 937 on 2009-01-31
Hi guys...
I've discovered Linux recently and I've been playing with Xbuntu on an old laptop. I wanted to try some games from Sourceforge.org (ezQuake). I,ve got a Tar.gz file on my desktop but what do I do with it now? There's no Setup.exe, do I need to run something from Terminal? 

I've played with a few bits... managed to get Xbuntu on a USB stick and I've tryed several distro CDs etc, all good stuff, I think I'm hooked.

---

### Post by taurus on 2009-01-31
First, you need to open a terminal and change to the directory where you've saved your .tar.gz.  Then, you have to unpack it.  It will probably create a new directory so you have to change to it and look at either README (Readme or readme) or INSTALL.  However, you can just run it from that new directory for some games by typing in the name of the file.

---

### Post by rksingh54 on 2009-02-01
> **taurus said:**
> First, you need to open a terminal and change to the directory where you've saved your .tar.gz.  Then, you have to unpack it.  It will probably create a new directory so you have to change to it and look at either README (Readme or readme) or INSTALL.  However, you can just run it from that new directory for some games by typing in the name of the file.
I have downloaded a file  OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz. I know how to navigate but I do not know command lines to unpack and install it in my root directory. If you would not mind, please provide instructions.

RKS

---

### Post by taurus on 2009-02-01
> **rksingh54 said:**
> I have downloaded a file  OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz. I know how to navigate but I do not know command lines to unpack and install it in my root directory. If you would not mind, please provide instructions.

RKS

Assuming you have saved it to your desktop, open a terminal and run

```
cd ~/Desktop
tar xvzf OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz
```
That would create a new directory and unpack it in there.  So, you have to change to that new directory and install them with the dpkg -i command.

```
cd OOo_3.0.1_LinuxIntel_install_en-US
sudo dpkg -i *.deb
```
Again, I assume the new directory is called OOo_3.0.1_LinuxIntel_install_en-US.  And if you're not sure the name, look at the output of this command after you have unpacked it.

```
ls -la
```

---

### Post by Vryko Lakas on 2009-02-01
> **taurus said:**
> Assuming you have saved it to your desktop, open a terminal and run

```
cd ~/Desktop
tar xvzf OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz
```
That would create a new directory and unpack it in there.
And just to expand the details a bit: 
Think of a tar.gz as a zipped archive.  It's like a .zip file for Linux and Unix. [Tar](http://en.wikipedia.org/wiki/Tar_(file_format)) is the kind of file format that collects the contents into an archive, and .gz means that it was compressed using [gzip](http://en.wikipedia.org/wiki/Gzip).

The letter x in the command is a flag which tells the tar program to "e**x**tract" the files from the tar.gz archive. 
The letter v tells it to be "**v**erbose," which means you get to read the play-by-play of the unpacking process. 
The letter z "un**z**ips" the file, which decompresses it. If you see a file ending in tar.**bz**, you would use j instead of z. (.bz files are compressed using [bzip](http://en.wikipedia.org/wiki/Bzip2) instead of gzip.) 
The final letter, f, just tells the program that the next string of symbols will be the name of the **f**ile to work with. In this case, the file to work with is OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz which you downloaded. 


And just by sheer coincidence, I happened to see this thread on the front page: 
[http://ubuntuforums.org/showthread.php?p=6639054#post6639054]("http://ubuntuforums.org/showthread.php?p=6639054#post6639054")
A guide for installing OpenOffice 3 using the file from the website. :)

---

### Post by rksingh54 on 2009-02-01
Thank you so much for that help 

RKS

---

### Post by rksingh54 on 2009-02-01
Thanks so much for the explanation and the URL.

RKS

---

### Post by adamlau on 2009-02-01
Decompression is one of those things where I prefer a GUI to the CLI. Install either Squeeze, or Xarchiver, or both (Xarchiver can handle passworded archives) and the thunar-archive-plugin :) .

---

### Post by xCel on 2009-02-02
There aren't any *.deb files in the package... I am trying to install this as well, and I'm a noob who wants to play quake again :)

If it helps, here's the link:
[http://ezquake.sourceforge.net/download/](http://ezquake.sourceforge.net/download/)

I unpacked it, but there is no readme or install or *.deb files. I tried just running the ezquake files, but nothing happens.

Please help :)

---

### Post by xCel on 2009-02-02
I'll explain better, I did

```

 ./ezquake-gl.glx 

```

and I got in return:

```

bash: ./ezquake-gl.glx: Permission denied

```

Whats that mean?! :(

Edit: 
```

Tried chmod -x ezquake-gl.glx

```

Now its saying 

```

Error: Couldn't load gfx/palette.lmp
```

---

### Post by taurus on 2009-02-02
Look at the fifth question from this page.

[http://ezquake.sourceforge.net/docs/?faq](http://ezquake.sourceforge.net/docs/?faq)

---

### Post by xCel on 2009-02-02
Great! Thank you.

I'm still working on it.. :)

---

