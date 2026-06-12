---
title: "How to run a game"
date: 2010-06-21
forum: Gaming &amp; Leisure
---

### Post by Praveen30 on 2010-06-21
I have just installed a game having file name trigger-0.5.2.1-src.tar.bz2.How to run it?

---

### Post by dim3000 on 2010-06-21
> **Praveen30 said:**
> I have just installed a game having file name trigger-0.5.2.1-src.tar.bz2.How to run it?

Don't do that, that's a source code zip which you need to compile yourself. Instead, if you want Trigger the racing game just search for trigger-rally in Synaptic or in a terminal:
```
sudo apt-get install trigger-rally
```

---

### Post by Praveen30 on 2010-06-21
ok,i have checked it and i have downloaded it.but it means everytime i can only play the games which are in repositories?

---

### Post by rizzeh on 2010-06-21
No, but it is much easier and safer to check for the game in repos first. Only failing that install manually.

---

### Post by Perfect Storm on 2010-06-21
Most games you'll find in the repositories - do also add playdeb: [http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)

Some games out there have their own .deb on their pages.
And most commercial games don't have .deb but many of them comes with an installation script.

---

### Post by del_diablo on 2010-06-21
> **Praveen30 said:**
> I have just installed a game having file name trigger-0.5.2.1-src.tar.bz2.How to run it?

tar.bz2 is a archive file, like .zip!
Likely either either of 2 options:
*Extract and use executeable
*the tarball contained sourcecode which needs to be compiled

---

### Post by nemiux on 2010-06-21
Easy, extract it lets say on desktop, then ```
cd /home/*/Desktop/Rally
``` Write ```
sudo make
``` and then ```
sudo make install
``` That should do the trick. Then somewhere in that folder you will find an executable

---

### Post by Mike'sHardLinux on 2010-06-21
hmmmm...

Ok, here's "really" how to compile Trigger (mostly).

*Please be aware that Trigger uses Jam instead of Make. (Make is the standard way, i.e. ./configure, make, sudo make install -- or better yet, sudo checkinstall).

First of all, you need these installed:
jam
libphysfs-dev
libalut-dev

```

sudo apt-get install jam libphysfs-dev libalut-dev

```

There may be more dependencies, but those are what I had to install to get this working. 

Be sure you have downloaded and extracted the main source AND the data. They are separate downloads.
[http://sourceforge.net/projects/trigger-rally/files/]("http://sourceforge.net/projects/trigger-rally/files/")

 I extracted the source, and then extracted the data files into the same folder as the source.

Now, onto the actual compiling....
```

cd ~/Desktop/trigger-0.5.2.1-src    #or wherever you extracted to
./configure
jam
sudo jam install

```

Once those steps are done:
```

./trigger

```


I still haven't figured it all out. It doesn't launch properly if I just type trigger, or if I run trigger from any other directory than where I compiled from. (I never used Jam before.) Any ideas?

---

