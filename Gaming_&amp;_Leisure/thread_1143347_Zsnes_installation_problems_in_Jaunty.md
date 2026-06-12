---
title: "Zsnes installation problems in Jaunty"
date: 2009-04-29
forum: Gaming &amp; Leisure
---

### Post by floatingpoint on 2009-04-29
I had problems with Zsnes crashing after upgrading to 9.04, so I uninstalled it in teminal

```
 $ sudo apt-get remove zsnes 
```

Then I restarted. 

I went to terminal, and...  

```
kevin@kevin-desktop:~$ sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate
kevin@kevin-desktop:~$ 

```

Went to Add/Remove, it won't let me check it to install.
Went to Synaptic, and when I mark it for installation I get
> zsnes:

Package zsnes has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


I went to software sources and checked some stuff in Third Party, then tried again, but I'm just getting the same problems.

Any help appreciated!

---

### Post by Perfect Storm on 2009-04-30
[http://packages.ubuntu.com/jaunty/i386/zsnes/download](http://packages.ubuntu.com/jaunty/i386/zsnes/download)

---

### Post by floatingpoint on 2009-04-30
Wrong architecture. I got it from apt-get in Intrepid?

---

### Post by Perfect Storm on 2009-04-30
> **floatingpoint said:**
> Wrong architecture. I got it from apt-get in Intrepid?

Wrong architecture? AFAIK zsnes is not available for 64-bit and ppc, only 32-bit.

---

### Post by floatingpoint on 2009-04-30
On my 64bit Intrepid Ibex I installed zsnes through terminal using apt-get, which is why I'm so confused. If there is only the intel version, perhpas I was running that. Is there away to bypass the wrong architecture error in the package installer?

---

### Post by Twitch6000 on 2009-04-30
I think you will need that program that helps you run 32 bit programs in order to install it.

I forget the name of it,but I am sure someone else will know.

---

### Post by floatingpoint on 2009-04-30
Is that the  x86-32 lib packages? How do I install those?

---

### Post by Perfect Storm on 2009-04-30
```
sudo apt-get install ia32-libs 
```

---

### Post by floatingpoint on 2009-04-30
```
kevin@kevin-desktop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java cacao-oj6-jre-headless java-common ttf-telugu-fonts
  ttf-bengali-fonts tzdata-java mbr libdvdread3 rhino ca-certificates-java
  ttf-kannada-fonts ttf-wqy-zenhei cacao-oj6-jre-lib ttf-oriya-fonts
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
kevin@kevin-desktop:~$ sudo apt-get install zsnes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate
kevin@kevin-desktop:~$ 

```

---

### Post by Grishka on 2009-04-30
zsnes was available for 64-bit intrepid, but is now gone from the repos, for reasons unknown ([https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/184255](https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/184255)). there are other options to get it working, though. simply running a 386 binary should work, as should installing zsnes deb from intrepid repos, or some ppa ([https://launchpad.net/ubuntu/+ppas?name_filter=zsnes](https://launchpad.net/ubuntu/+ppas?name_filter=zsnes)).
ah yes, to install a 386 deb on a 64-bit system, use "dpkg -i --force-architecture".

---

### Post by floatingpoint on 2009-04-30
Grishka, thanks very much for this information. So I would add the intrepid repo in software sources? what's the address I enter?

If that doesn't work I'll have a bash at forcing it.

---

### Post by Grishka on 2009-04-30
> **floatingpoint said:**
> Grishka, thanks very much for this information. So I would add the intrepid repo in software sources? what's the address I enter?

If that doesn't work I'll have a bash at forcing it.

no, no, don't add the intrepid repo to your sources. simply download the package from [http://packages.ubuntu.com/intrepid-updates/zsnes](http://packages.ubuntu.com/intrepid-updates/zsnes). try the one for amd64 first. if it won't work, get the 386 version and install with dpkg. --force-architecture is no big deal, it won't break your system or anything like that.

---

### Post by floatingpoint on 2009-04-30
Good hour or two of BOF without any problem. Thanks everybody!

---

### Post by luiz.gregorio on 2009-04-30
I got a successful installation on my Jaunty 64bits getting the package from [http://packages.ubuntu.com/intrepid-updates/zsnes](http://packages.ubuntu.com/intrepid-updates/zsnes)

Thanks for the info

---

### Post by floatingpoint on 2009-05-01
Yeah that's how I got it. Just to clarify for anyone who comes across this thread trying to solve the same problem; go to the link in the above post, download the file from one of the mirror links on that page, and open the file with the package manager. Sorted!

---

### Post by trugate on 2009-06-14
I'm trying to follow the link but it's no longer there.  I search for zsnes at that site and only find i386 packages.  Is there a reason why zsnes packages keep disappearing all over the place???

I dont care if I run the 32-bit version of zsnes in my amd64 install of 9.04, so long as I can get it working and use it.  I hate snes9x.

Any other ideas?  I've tried compiling it with forcing cpu architecture, etc, and after everything I try I only receive the error 'segmentation fault'.  

Using getlibs it says I've got all the libraries for the program.

Anyway, any simple deb files for 9.04 64-bit anywhere that someone may have compiled?

---

### Post by Grishka on 2009-06-15
> **trugate said:**
> I'm trying to follow the link but it's no longer there.  I search for zsnes at that site and only find i386 packages.  Is there a reason why zsnes packages keep disappearing all over the place???

I dont care if I run the 32-bit version of zsnes in my amd64 install of 9.04, so long as I can get it working and use it.  I hate snes9x.

Any other ideas?  I've tried compiling it with forcing cpu architecture, etc, and after everything I try I only receive the error 'segmentation fault'.  

Using getlibs it says I've got all the libraries for the program.

Anyway, any simple deb files for 9.04 64-bit anywhere that someone may have compiled?

I keep ZSNES for jaunty in [my PPA](https://launchpad.net/~thir/+archive/ppa). note that you'll still have to run it once with "-ad sdl", to keep it from segfaulting.

---

### Post by trugate on 2009-06-15
I've used apt-get purge zsnes* and then ran your amd64 deb package in your ppa.  When I ran it via terminal 'zsnes -ad sdl' it gave me segmentation fault...  I'm new, and although I've searched and tried to figure out what that error means, I'm not sure what to try.  

If you're out of ideas that's okay, I'm going to search and work at this until zsnes is running natively in linux.  I also tried running it via wine (my old windows version) and surprisingly it locks up, and last time I was using ubuntu (7.10) it worked fine through there...  but anyway, any input would be great if you got anything.

Thanks for the link to your ppa!

---

### Post by trugate on 2009-06-16
I got tired of running into problem after problem with 64-bit, so here I am with 32-bit 9.04, and there's zsnes in the repo, installed and running without a hitch.  I don't notice much speed difference between the two with what I do, so I'm happy.  I wish I knew enough to contribute and solve the issue, so that it COULD be simply listed in the repo for amd64.  

I hope it gets fixed/simplified someday.

---

### Post by garytr23 on 2009-07-13
There is a reason this is difficult.  Many portions of zsnes are still hand-coded in assembly language, 32-bit assembly language, so it's very hard to make a native 64-bit version.  

Try bsnes, it's a cycle-accurate simulator so it runs slow compared to zsnes, but once they add an emulated chip, they don't have to do any hacks to add support for particular games as the hardware is emulated perfectly.  Also, it's all written in C++ so it's portable and cross-platform.  It has been quickly improving, and they just recently added support for the superfx and SA-1 chips.  But the main goal isn't to play games, it's a like a hardware documentation project, similar to MAME's goals.

[http://byuu.org/bsnes/](http://byuu.org/bsnes/)

---

### Post by garytr23 on 2009-07-15
There's also a new gtk+ port of snes9x you should check out.  Got started a month ago.

[http://code.google.com/p/snes9x-gtk/](http://code.google.com/p/snes9x-gtk/)

---

### Post by mister_playboy on 2009-07-20
> **luiz.gregorio said:**
> I got a successful installation on my Jaunty 64bits getting the package from [http://packages.ubuntu.com/intrepid-updates/zsnes](http://packages.ubuntu.com/intrepid-updates/zsnes)

Thanks for the info

Package works great for me, too!  I never did get zsnes running properly on 8.10, but this worked for me on the first go.  Sound is a just a bit choppy, but it's working with PulseAudio...(!!!) :guitar:

Awesome!  :D

---

