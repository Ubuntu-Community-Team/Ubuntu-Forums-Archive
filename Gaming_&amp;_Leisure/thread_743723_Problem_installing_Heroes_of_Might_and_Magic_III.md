---
title: "Problem installing Heroes of Might and Magic III"
date: 2008-04-02
forum: Gaming &amp; Leisure
---

### Post by Alucard-sama on 2008-04-02
Recently I got a copy of Heroes of Might and Magic III and an old garage sale.
I ripped it to an iso to prevent data loss and mounted the iso to /media/iso.
When I try to run setup.sh this happens:

> root@Ken-Linux:~# cd /media/iso
root@Ken-Linux:/media/iso# sh setup.sh
setup.sh: 9: function: not found
x86
root@Ken-Linux:/media/iso# 


---

### Post by erginemr on 2008-04-03
Is there really a HOMM-3 version for Linux? If so, is there a "setaup.sh" file in the /media/iso folder? If your answer to both is yes, then the following might work:
```
cd /media/iso
sh ./setup.sh
```

---

### Post by riteandritual on 2008-12-21
I had this problem too! The great thing about Lokigames.com are the linux versions they made, and I was so upset I couldn't get this classic to install.

This is what worked for me:

```
sudo apt-get install ksh
sudo ksh setup.sh
```

---

### Post by MaximB on 2008-12-23
The one truly upsetting thing about HOMM3 and Linux is that they made a Linux client to only the first HOMM3 and not the expansions  that came afterwords that gives you a map generator which makes the game endless , not to mention a new town.

---

### Post by qrwe on 2009-02-13
My problem is when trying to apply the patches:
```

bash heroes3-1.3.1a-unified-x86.run 
Uncompressing Heroes of Might and Magic III 1.3.1a Update......................................
gzip: stdin: unexpected end of file

loki_patch: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted
The program returned an error code (1)

```
This is also after correcting some syntax errors in the preceding bash script and removing the MD5 check, which made the patch totally unusable. These changes didn't make anything with the patch content over all though. Any ideas what has gone wrong?

---

### Post by blacksm1th on 2009-04-11
> **qrwe said:**
> ...
Try this if your Ubuntu is x64:
Extract the patch:
```
# _POSIX2_VERSION=199209 ./heroes3-1.3.1a-unified-x86.run --keep
```
PATCH the patch :)
1.get the fixed "loki_patch" file
```
# wget http://icculus.org/~msphil/loki/x86/loki_patch
```
2.then overwrite "loki_patch" here /heroes3-1.3.1a-unified-x86/bin/Linux/x86/loki_patch
3.make "loki_patch" executable
4.start patched patch and answer the questions:
```
# linux32 ./update.sh
```
5.check heroes version
```
# ./heroes3 --version
Heroes of Might & Magic III 1.3.1a
Built with glibc-2.1 on x86


```

This explanation is not for begginers because i use mostly nautilus and only if there is no other way - terminal.

EDIT: if you want it in window:
```
# ./heroes3 -w
```

---

### Post by jdunn on 2009-04-11
> **erginemr said:**
> Is there really a HOMM-3 version for Linux? If so, is there a "setaup.sh" file in the /media/iso folder? [/code]

Yes, I own a copy I bought from Loki years ago.  I haven't installed it in years.

---

### Post by yaroto98 on 2009-04-11
I got the win-doze version to work just fine in Wine.

Not sure if you want to take that path, but it does work.

#wine /media/iso/Heroes3.exe

---

### Post by Alucard-sama on 2009-06-03
> **riteandritual said:**
> I had this problem too! The great thing about Lokigames.com are the linux versions they made, and I was so upset I couldn't get this classic to install.

This is what worked for me:

```
sudo apt-get install ksh
sudo ksh setup.sh
```

Okay progress.
Sorry I've let this thread lay dead so long, just tried to install it again, after using the above method I managed to get further than before only to be harshly reminded I'm using x64 =P

```
This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at support@lokigames.com
```

I'm pretty sure there are ways to get it working on x64, any help would be GREATLY appreciated.

---

### Post by Grishka on 2009-06-03
check out [vcmi](http://antypika.aplus.pl/vcmi/forum/portal.php). it's not yet fully functional, but it's getting better all the time.

---

### Post by Alucard-sama on 2009-06-03
> **Grishka said:**
> check out [vcmi](http://antypika.aplus.pl/vcmi/forum/portal.php). it's not yet fully functional, but it's getting better all the time.

Cheers, looks pretty good, but quite incomplete, was wanting to play now rather than in a year or two's time, so if anybody has a solution to mein new problem?

---

### Post by Grishka on 2009-06-03
loki patches are notorious for not working nowadays. sorry to say that, but your best bet is running the windows version under wine. the upside is that WoG will work as well.

---

### Post by crazyfuturamanoob on 2009-06-05
> **Alucard-sama said:**
> Recently I got a copy of Heroes of Might and Magic III and an old garage sale.
I ripped it to an iso to prevent data loss and mounted the iso to /media/iso.
When I try to run setup.sh this happens:
> root@Ken-Linux:~# cd /media/iso
root@Ken-Linux:/media/iso# sh setup.sh
setup.sh: 9: function: not found
x86
root@Ken-Linux:/media/iso# 

Why are you logged in as root?

---

### Post by Alucard-sama on 2009-06-06
> **crazyfuturamanoob said:**
> Why are you logged in as root?

It doesn't grant me permission to run it unless I am.

---

### Post by rettichschnidi on 2009-06-09
Have you tried the new LIFLG installer[1]? Feedback is appreciated. 

[1]: [http://liflg.org/forum/viewtopic.php?t=938](http://liflg.org/forum/viewtopic.php?t=938)

---

### Post by arnasd on 2009-06-13
hello,

i have encountered strange error trying to launch heroes3:
when i launch it as simple user ( ./heroes3 ), it loads up and says that there is no free space on my disk, while there is way more free space than 5mb (minimum requirement).

[[IMG]http://img191.imageshack.us/img191/1135/heroes3notenoughspaceer.png[/IMG]](http://img191.imageshack.us/i/heroes3notenoughspaceer.png/)


i thought that something is wrong with permissions, but i can not launch the executable as sudo:

> ard@ard:~/games/Heroes3$ sudo ./heroes3
X Error:  137
  Request Major code 131 (XFree86-DGA)
  Request Minor code 1 ()
  Error Serial #17
  Current Serial #17


how can i solve this problem?

thanks.

---

### Post by arnasd on 2009-06-16
Problem solved.

I just had to delete /home/$user$/.loki directory, because game could not write into it (it was created as sudo).
Started the game again, and it worked.

---

### Post by HOMM3Player on 2010-11-30
I can see this is an old thread, but it came up in a google search when I went to re-install Heroes of Might and Magic 3 recently. I succeeded in getting it working on a recent HP laptop with Ubuntu 10.04 (Lucid Lynx). Here is the procedure I used (for posterity):

1. Insert HOMM3 CD, navigate to the setup.data/bin/x86/glibc-2.1 directory
2. Copy the "setup" file to a temporary directory: /home/you/tmpsetup/setup
3. Make sure the directory is executable: chmod 700 /home/you/tmpsetup/
4. **Now you need an old version of libgtk**: libgtk1.2.
4a. This personal package archive (PPA) had libgtk1.2 as of Nov. 2010:
[https://launchpad.net/~adamkoczur/+archive/gtk1.2](https://launchpad.net/~adamkoczur/+archive/gtk1.2)
4b. Add the above PPA to your software sources, in Software Sources-->Other software tab, add "deb [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu) lucid main"
4c. Reload sources (option given after trying to close software sources).
4d. Open Synaptic Package Manager and install the libgtk1.2 package (will automatically include some others).
5. Making sure you are in the HOMM3 CD top level directory, run the setup program as root: sudo /home/you/tmpsetup/setup
6. Now download and decompress the patch:
6a. Download the patch (as of Nov. 2010, it appears to be at ftp://mirrors.dotsrc.org/lokigames/updates/heroes3/heroes3-1.3.1a-unified-x86.run"
Note: You may be able to use ksh to just run the patch (./update.sh). If you don't have ksh installed or wish to do this manually, follow the remaining steps:
6b. Create a temporary directory: mkdir heroes3-1.3.1a-unified-x86
6c. Enter that directory: cd heroes3-1.3.1a-unified-x86
6d. Decompress the patch: tail -n +177 ../heroes3-1.3.1a-unified-x86.run | gzip -cd | tar xvf -
7. Now patch the install:
7a. sudo bin/Linux/x86/loki_patch patch.dat /usr/local/games/Heroes3/
Note: this may return an error "loki_patch: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed." However, the update should have correctly updated the heroes3 and heroes3.dynamic executables, and added 3 README files.
8. Play Heroes3!

---

