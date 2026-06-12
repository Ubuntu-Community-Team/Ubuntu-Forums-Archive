---
title: "How DO I Uninstall World of Padman?"
date: 2007-08-02
forum: Gaming &amp; Leisure
---

### Post by DMXell on 2007-08-02
Okay, so I installed the game World of Padman, tried it out and just thought it wasn't worth the 500 MB of space it was taking up. So I tried to remove it. First I tried its own uninstall program and to no avail. Then I scoured the Synaptic Package Manager and can't find it in there. And as a last resort I searched here but cannot find it. Can anyone help me out? Thanks.

Oh yeah, and I tried several terminal variations and they all looked like this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wop

---

### Post by dreadlord_chris on 2007-08-02
> **DMXell said:**
> Okay, so I installed the game World of Padman, tried it out and just thought it wasn't worth the 500 MB of space it was taking up. So I tried to remove it. First I tried its own uninstall program and to no avail. Then I scoured the Synaptic Package Manager and can't find it in there. And as a last resort I searched here but cannot find it. Can anyone help me out? Thanks.

Oh yeah, and I tried several terminal variations and they all looked like this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wop

How did you install it?

---

### Post by DMXell on 2007-08-02
> **dreadlord_chris said:**
> How did you install it?

There was documents on how to install on this sit: [http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php)

They just changed their theme and I can't find the documents again however. It's the off-site link on the main page of ubuntuforums.org

---

### Post by hikaricore on 2007-08-02
> $ ls -la
total 2488
drwxr-xr-x  6 hikaricore hikaricore    4096 2007-04-01 12:27 .
drwxrwxr-x 98 hikaricore hikaricore    4096 2007-08-02 01:40 ..
-rw-r--r--  1 hikaricore hikaricore    1324 2007-04-01 12:26 copyright_en.txt
-rw-r--r--  1 hikaricore hikaricore   17996 2007-04-01 12:26 gpl.txt
drwxr-xr-x  3 hikaricore hikaricore    4096 2007-04-01 12:27 .manifest
drwxr-xr-x  3 hikaricore hikaricore    4096 2007-04-01 12:26 readme
-rw-r--r--  1 hikaricore hikaricore     509 2007-04-01 12:26 README
-rw-r--r--  1 hikaricore hikaricore     755 2007-04-01 12:26 readme.html
-rwxr-xr-x  1 hikaricore hikaricore    1643 2007-04-01 12:27 **uninstall**
drwxr-xr-x  2 hikaricore hikaricore    4096 2007-06-10 19:47 wop
-rwxr-xr-x  1 hikaricore hikaricore     885 2007-04-01 12:26 WoP
-rwxr-xr-x  1 hikaricore hikaricore  791553 2007-04-01 12:26 wopded.i386
-rwxr-xr-x  1 hikaricore hikaricore 1674978 2007-04-01 12:26 wop-engine.i386
-rw-r--r--  1 hikaricore hikaricore    2088 2007-04-01 12:26 wop.png
drwxr-xr-x  2 hikaricore hikaricore    4096 2007-04-01 12:26 xtras


The game appears to have it's own uninstaller now that you've cleared up that you didn't install it as a package...

I suggest locating your WoP directory as such:

```
locate WoP
```

You should be able to track it down.

---

### Post by edemark on 2007-08-02
hi 
i would try to start installer again to know where the game gets installed (of course supposing that you have accepted default setting for install) cancel install then browse to the directory where the game is allready installed and delete it.

---

### Post by DMXell on 2007-08-03
I know where it's installed, and I said that I already tried the games uninstaller (it failed to open, I tried six or so different times)... So I should just go into root and drag the folder to the trashcan and empty? Coming from a Mac OS X and Windows background I typically hate doing this since many programs tend to place some files in certain sections of the OS and I want to get rid of those as well.

---

### Post by hikaricore on 2007-08-03
> **DMXell said:**
> I know where it's installed, and I said that I already tried the games uninstaller (it failed to open, I tried six or so different times)... So I should just go into root and drag the folder to the trashcan and empty? Coming from a Mac OS X and Windows background I typically hate doing this since many programs tend to place some files in certain sections of the OS and I want to get rid of those as well.

You ran the installer with **sudo** you'll need to do the same with the uninstaller.

You can probably remove the folder manually and be fine, but there will be a few symlinks around and perhaps a few data files in /usr/share somewhere.
This is not windows land, _Normally_ applications in Linux do not install &@^$ in ridiculous places.

---

### Post by DMXell on 2007-08-03
I also said Mac OS X (my preferred OS) which is, hello, *knock on head* Unix-based. Windows is a crappy OS, I was just using it as an example.

Now, I'm not entirely familiar with a lot of the terminal commands. I tried to run the uininstaller but this is what happened:

william@ubuntu:~$ sudo /usr/local/games/WoP/uninstall
Could not find a usable uninstall program. Aborting.

I'm pretty sure I entered the wrong command here, so any idea how I'm supposed to do it?

---

### Post by Zzl1xndd on 2007-08-03
WoP installs everything by default in your Home directory. Now perhaps I'm crazy and I'm sure someone will tell me if I am but you should be able to just delete the Folder. (the installer was a .Run)

---

### Post by Sindwiller on 2007-08-03
> I'm pretty sure I entered the wrong command here, so any idea how I'm supposed to do it?

Or your WoP installation is b0rked. Anyway, you could just redownload the installer, install it again (or check if it has an uninstall function; **or**, you could force the installer to extract the stuff only and check for the uninstaller - either way, consider the --help output)

---

### Post by forrestcupp on 2007-08-26
> **tweakedenigma said:**
> WoP installs everything by default in your Home directory. Now perhaps I'm crazy and I'm sure someone will tell me if I am but you should be able to just delete the Folder. (the installer was a .Run)

That is correct.  The game binaries and files are installed to your home directory and not to your system.  Anything that is only installed to the home directory is safe to just delete.  They do it this way so that it will run on any distro.  If they packaged it to install to the system, it would be distro specific and it would be more of a pain for them.

So the solution for this particular game is to just delete the directory in your home folder, and you'll be rid of your game.  It also installs a startup script in your /home/username directory called wop.  You can delete that too if you want.

---

### Post by TheGZeus on 2007-11-21
I ran the installer as root (I got used to installing programs as root. sudo apt-get...) and now it's spread througout my system and the uninstaller is useless.
I'd like to remove it, or at least re-install it(as a user).
HELP!
Right now it seems I need to either run a game as root (shudder), never retain any game settings(my ATI Mobility can barely run the game at ALL and I need to turn off some things...), or leave a gig or so of data laying aroud in my system...

in this day and age not having a .deb or at least a .rpm file is rather strange...

(P.S. I really don't want to be a dick, but I'm ludicrously stressed out at this moment. I'm in an autistic panic over having no idea how to remive this from my computer and I REALLY don't want to re-install as I've customised this isntallation enough I would lose a good 5-8 hours of my life...

---

### Post by MichiganMan on 2007-12-10
> **TheGZeus said:**
> 
(P.S. I really don't want to be a dick, but I'm ludicrously stressed out at this moment. I'm in an autistic panic over having no idea how to remive this from my computer and I REALLY don't want to re-install as I've customised this isntallation enough I would lose a good 5-8 hours of my life...

I feel for you.  Been there.  just curious, would you have possibly put your .home on its own partition when you installed?  If so, then you can safely re-install, taking care not to format your ./home partition, and not lose most if any of your configuration.  

I recommend this technique to anyone installing a linux distro.  I just made very good use of it after a video driver installation gone bad borked my install.  Reinstalled Ubuntu, reinstalled my chosen apps, (ok, thats a minor pain) and I was back in business, bookmarks, wallpaper, emails and all.

---

### Post by Michalxo on 2009-12-24
I think it uses loki-installer, uninstaller and I don't have it. I am experiencing the same bug as you do. I already wrote on their forum. Let's wait for their reaction.

[http://padworld.myexp.de/forum/viewtopic.php?f=14&t=5172](http://padworld.myexp.de/forum/viewtopic.php?f=14&t=5172)

^^ there is all the necessary info to successful removing of World of Padman out of your system ;-)

---

