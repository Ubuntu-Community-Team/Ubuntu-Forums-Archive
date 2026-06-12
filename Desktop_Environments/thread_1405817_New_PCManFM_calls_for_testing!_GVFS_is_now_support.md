---
title: "New PCManFM calls for testing! GVFS is now supported."
date: 2010-02-13
forum: Desktop Environments
---

### Post by PCMan on 2010-02-13
Hello,
I'm the main developer of the desktop environment LXDE and its file manager, PCManFM.
After six months of developement, here I'm glad to announce that the next generation PCManFM calls for testing.
This is not a revision, but a total rewrite based on glib/gio and also supporting gvfs.
It's almost time to have the first public alpha release. So I'm here to call for testing and we can fix the bugs according to user feedback. This might be included in Lubuntu, too. So please help us.

Main changes:
1. remote file systems are now accessible within pcmanfm. (requires gvfs)
2. trash can is now working. (requires gvfs)
3. desktop management is re-written (not yet finished)
4. Better compatibility with other DEs
5. Some features are now lacking because this is a total rewrite from scratch and the source code is not based on the original pcmanfm 0.5 series.
6. While supporting gio and gvfs, pcmanfm2 didn't become heavy. Its performance is still as good as the original pcmanfm 0.5 series. :-) Don't argue with me before you try it. To see is to believe.
7. The core of the file manager now becomes a separate library called libfm. It can be used by other programs requiring file management facilities. (Yes, it's possible to develop your own two-pane-layout file manager based on libfm.)

You can grab the latest source code in development for testing and previewing from the git repo with following command line.
Source code of libfm (required to compile pcmanfm):
```
git clone git://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/libfm
```

Source code of new pcmanfm (This is a total re-write. If you need source code of old deprecated pcmanfm series, please check it out from svn repository.):
```
git clone git://pcmanfm.git.sourceforge.net/gitroot/pcmanfm/pcmanfm
```

Please install libfm before compiling pcmanfm. Libfm itself brings an standalone demo program named libfm-demo, which could work as a minimal file manager. Both libfm and pcmanfm can be compiled with following commands:
```

./configure --sysconfdir=/etc
make
sudo make install
```

More details:
[http://blog.lxde.org/](http://blog.lxde.org/)
[http://blog.lxde.org/?p=601](http://blog.lxde.org/?p=601)

Please read [http://blog.lxde.org/](http://blog.lxde.org/) to get latest news about LXDE.

---

### Post by mac9416 on 2010-02-13
Hey, PCMan,

If I get this to work, it will be the first time I have ever successfully compiled any software. I'm new to Linux and addicted to APT.

So I managed to get the source with git. But when I cd into libfm and try to run ./configure, I find that there is no configure file. What am I missing?

Thanks!

---

### Post by Darkblood on 2010-02-21
> **mac9416 said:**
> Hey, PCMan,

If I get this to work, it will be the first time I have ever successfully compiled any software. I'm new to Linux and addicted to APT.

So I managed to get the source with git. But when I cd into libfm and try to run ./configure, I find that there is no configure file. What am I missing?

Thanks!

I'm having the same problem.

---

### Post by halfvulcan on 2010-02-24
Pcman, you're the man. I'm one of those who wanted a trashcan, because of the occasional "oh #$%!, I didn't mean to delete that!"  Mistakes happen even among pros.  Feature request?:  directory tree and locations panes visible simultaneously would be amazing.  Alternatively if that's not doable, maybe add removable drives to bookmarks or tree view, so I never have to leave tree view to mount a thumb drive?
Love your file+desktop manager.  Starts up fast, low resource usage, well-picked featureset, attractive simple interface...  You do great work.  Thanks so much.

---

### Post by koleoptero on 2010-02-24
*Finally* support for trash. :D Thank you tons for this amazing file manager by the way. I just love its speed and versatility.

---

### Post by Darkblood on 2010-02-28
I was able to configure and install libfm. But i only could configure pcmanfm, when i do make i get some errors.

Can anyone help?

---

### Post by MonsterTrimble on 2010-03-13
> **Darkblood said:**
> I'm having the same problem.

The ling PCMan provided gives an incomplete package. Go to his sourceforge page and get the newest versions.

---

### Post by MonsterTrimble on 2010-03-13
Don't bother. There's no makefile.

---

### Post by kerry_s on 2010-03-13
why not just use the ppa?
[https://launchpad.net/~lxde/+archive/ppa](https://launchpad.net/~lxde/+archive/ppa)

---

### Post by mac9416 on 2010-03-13
> **kerry_s said:**
> why not just use the ppa?
[https://launchpad.net/~lxde/+archive/ppa](https://launchpad.net/~lxde/+archive/ppa)

Looks like that PPA has the "original" 0.5 PCManFM, and not the complete rewrite.

---

### Post by kerry_s on 2010-03-13
> **mac9416 said:**
> Looks like that PPA has the "original" 0.5 PCManFM, and not the complete rewrite.

i missed that part:
> 5. Some features are now lacking because this is a total rewrite from scratch and the source code is not based on the original pcmanfm 0.5 series.

sorry.

---

### Post by MonsterTrimble on 2010-03-13
I'm confused on this though. I know on the Lubuntu page they said 0.9 was going in, yet I haven't seen hide nor hair of it.

And it's annoying because I really want to like PCManFM. And since it looks like it solves the filesharing issues in 0.5 I really want it.

---

### Post by VCoolio on 2010-03-14
Seems promising! I got it to work (run ./autogen.sh first; also install / compile dependencies libfm and menu-cache). But I can't browse network shares; pcmanfm complains about those folders not being mounted:
```
** (pcmanfm2:23605): DEBUG: FmJob error: The specified location is not mounted
```
Isn't the filebrowser supposed to do that itself? That's how nautilus and thunar work at least, I think. Or is this a permissions issue again? Also it will need to have the feature to add actions to the context menu of files / folders if I'm to use pcmanfm. But keep up the good work.

---

### Post by PCMan on 2010-03-14
> **VCoolio said:**
> Seems promising! I got it to work (run ./autogen.sh first; also install / compile dependencies libfm and menu-cache). But I can't browse network shares; pcmanfm complains about those folders not being mounted:
```
** (pcmanfm2:23605): DEBUG: FmJob error: The specified location is not mounted
```
Isn't the filebrowser supposed to do that itself? That's how nautilus and thunar work at least, I think. Or is this a permissions issue again? Also it will need to have the feature to add actions to the context menu of files / folders if I'm to use pcmanfm. But keep up the good work.

I guess trash:///, sftp:///, and others don't work either.
If this is the case, it seems that your gvfs is not functioning correctly, which in turns can be a dbus-related problem.
Please make sure that you have gvfs-backends installed and dbus is running.

---

### Post by hhh on 2010-03-14
Hi, did an option to hide the "My Documents" folder on the desktop make it into this version? Also, I'm on Karmic and I'm getting dependency errors trying to configure the latest libfm (intltools, which I installed on top of intltools-debian, but I'm stuck on needing gtk+-2.0). Suggestions?

---

### Post by VCoolio on 2010-03-14
> **PCMan said:**
> I guess trash:///, sftp:///, and others don't work either.
If this is the case, it seems that your gvfs is not functioning correctly, which in turns can be a dbus-related problem.
Please make sure that you have gvfs-backends installed and dbus is running.

Thanks for replying. trash:/// works; gvfs-backends is installed with version 1.4.1-0ubuntu1; dbus is running. It's right about the targets not being mounted btw, if they are, it can browse them. But thunar or nautilus mount stuff when clicked automatically.

---

### Post by hhh on 2010-03-17
bump

---

### Post by kerry_s on 2010-03-17
@PCMan, 
i got the lubuntu alpha3 with PCManFM 0.9.2, when i right click to empty the trash it does nothing, but i can go to the trash folder, select everything in it & delete. is that a known issue?

---

### Post by walterav on 2010-03-20
Complete compile/build howto:

[http://wiki.lxde.org/en/index.php?title=PCManFM_build_and_setup_guide](http://wiki.lxde.org/en/index.php?title=PCManFM_build_and_setup_guide)

:popcorn:

---

