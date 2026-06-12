---
title: "Audio problem with Heroes of Might and Magic 3 on Ubuntu 10.10"
date: 2010-12-11
forum: Gaming &amp; Leisure
---

### Post by ryu kun on 2010-12-11
Hello,

I get this error in terminal when I run heroes3: "Couldn't open audio: "

It's patched:

```
 heroes3 -v
Heroes of Might & Magic III 1.3.1a
Built with glibc-2.1 on x86
```

I am not sure but I guess this issue can be related with OSS. I am using Ubuntu 10.10. I've tried to run the game with "padsp heroes3" command but it didn't change anything.

Any suggestions other than using Ubuntu 10.04, please?

---

### Post by iMihael on 2011-01-01
I have the same problem. I think sound doesn't work because Heroes using OSS as sound system, but Ubuntu use pulseaudio. Now we have a question, how to solve this sound problem ?? Please anybody help!!

---

### Post by kDDs on 2011-02-02
Not sure if anyone wants to know the solution to the sound problems, but here goes (I understand most threads on the subject are months, if not years old).

This was winding me up to no end recently. I tried more or less everything without tearing the kernel apart, but finally found a rather simple and elegant solution...

First of, download the compatibility pack I've uploaded from:

[http://www.megaupload.com/?d=AQZAG5Y0](http://www.megaupload.com/?d=AQZAG5Y0)

(If anyone could host this on a more permanent basis, that would be ideal!)

Next, extract and place in:

```
/usr/local/lib
```

So, if you "ls" /usr/local/lib you should see the folder "Loki_Compat" and a python* one.

To launch the game;

```
LD_PRELOAD=/usr/local/lib/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/local/lib/Loki_Compat/libsmpeg-0.4.so.0.1.3:/usr/local/lib/Loki_Compat/libsmjpeg-0.2.so.0:/usr/local/lib/Loki_Compat/libSDL_mixer-1.2.so.0 '/location/of/heroes3.dynamic' -w

```

Where "/location/of/heroes3.dynamic" is the location of heroes3.**dynamic** (not the default heroes3)

The -w will run the game windowed, which I suggest doing to make sure it'll work, it can be removed after if you'd rather play full screen.

I hope someone reads this and it helps at least one person! I'd always rather play the game native than through wine!

(this was tested on linux mint julia on two separate eee pc 901)

---

### Post by Armichiels on 2011-03-21
Many thanks! 
It works fine for me! Now you know it was usefull for me at least!
I just had to change the version numbers of libsmjpeg and libSDL_mixer in the command line to launch the game :```
LD_PRELOAD=/usr/local/lib/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/local/lib/Loki_Compat/libsmpeg-0.4.so.0.1.3:/usr/local/lib/Loki_Compat/libsmjpeg-0.2.so.0.0.1:/usr/local/lib/Loki_Compat/libSDL_mixer-1.2.so.0.2.5 /usr/local/games/Heroes3/heroes3.dynamic -w

```
Thanks again!

---

### Post by perito on 2011-06-20
anyone knows where I can find the compatibility pack ? the link became invalid ...

---

### Post by crimilde on 2011-11-19
> **perito said:**
> anyone knows where I can find the compatibility pack ? the link became invalid ...

I had the same issue when trying to play and I found the compatibility libs here:

[http://www.swanson.ukfsn.org/loki/](http://www.swanson.ukfsn.org/loki/)

---

### Post by Gnee on 2012-02-23
Hi,

I've been trying to run Heroes3 with sound since yesterday, and eventually I tried the solution explained in this thread. Problem is, I don't have a "heroes3.dynamic" file anywhere... Did I miss something?

Thx :)

---

### Post by Subidubi32 on 2012-03-26
Now the audio is fine, but if I launch the game in full screen, its out of range.. How could I change resolution, or refresh rate?

---

### Post by vananematu on 2013-03-12
> **crimilde said:**
> I had the same issue when trying to play and I found the compatibility libs here:

[http://www.swanson.ukfsn.org/loki/](http://www.swanson.ukfsn.org/loki/)


Superb!

To conclude the installation of HOMM3 on ubuntu 12.10 or newer or earlier a bit:

1. Mount the god damn iso or copy the installation contents to /path/somewhere

2. ~/path/HOMM3_setup/linux32 bash setup.sh 
   or 
   ~/path/HOMM3_setup/linux32 sh setup.sh
   perhaps even without "linux32" depending on your configuration. I for instance had to use it.

3. To update: (relevant thread - [http://wtanaka.com/node/7641](http://wtanaka.com/node/7641))

wget [ftp://mirrors.dotsrc.org/lokigames/updates/heroes3/heroes3-1.3.1a-unified-x86.run](ftp://mirrors.dotsrc.org/lokigames/updates/heroes3/heroes3-1.3.1a-unified-x86.run)

 _POSIX2_VERSION=199209 ./heroes3-1.3.1a-unified-x86.run --keep

 Download manually [http://downloads.sourceforge.net/goldenfiles/loki_patch-fix-0.1.tar.gz](http://downloads.sourceforge.net/goldenfiles/loki_patch-fix-0.1.tar.gz)

 unzip the archive of the patch fix and copy:

 cp Loki_patch-fix/fixedpatch heroes3-1.3.1a-unified-x86/bin/Linux/x86/loki_patch

 linux32 bash heroes3-1.3.1a-unified-x86/update.sh

4. NO SOUND

 Download old libraries and unzip: [http://www.swanson.ukfsn.org/loki/](http://www.swanson.ukfsn.org/loki/)
 
 cd Heroes3
 cp /path/Loki_Compat /path/Heroes3
 LD_PRELOAD=Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:Loki_Compat/libsmpeg-0.4.so.0.1.3:Loki_Compat/libsmjpeg-0.2.so.0.0.1:Loki_Compat/libSDL_mixer-1.2.so.0.2.5 /home/user/Games/Heroes3/heroes3.dynamic
 add "-w" to the end of last line to use windowed mode.

I didn't have problems with resolution.

Using Ubuntu Studio 12.10 x86_64 with kernel 3.8.1 with latest AMD official 13.1 videocard drivers.

Relevant threads:

[http://ubuntuforums.org/showthread.php?t=1643092](http://ubuntuforums.org/showthread.php?t=1643092)

[http://ubuntuforums.org/showthread.php?t=1947686](http://ubuntuforums.org/showthread.php?t=1947686)

To update kernel and videocard drivers easily:

[http://www.upubuntu.com/2013/02/installupgrade-to-linux-kernel-38.html](http://www.upubuntu.com/2013/02/installupgrade-to-linux-kernel-38.html)

[http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html](http://www.upubuntu.com/2013/01/amd-catalyst-display-driver-131-adds.html)

---

### Post by wildmanne39 on 2013-03-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

