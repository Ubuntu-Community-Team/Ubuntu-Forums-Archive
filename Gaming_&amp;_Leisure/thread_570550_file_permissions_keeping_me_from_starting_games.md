---
title: "file permissions keeping me from starting games"
date: 2007-10-08
forum: Gaming &amp; Leisure
---

### Post by deruberhanyok on 2007-10-08
Hello Ubuntu gurus,

I've been running Ubuntu as my main OS since Feisty was released (and I'm very much looking forward to Gutsy and trying it out in 64-bit mode). It has taken everything I've thrown at it without issue, and I've been content to boot into Windows to play some games.

I did have a few games running through WINE at one point but decided it would be easier to just continue dual-booting for now. I decided I'd take one of the games I play regularly (UT 2004) and give it a try under Linux; after all, UT3 is coming out soon and I'd like to avoid playing it in Windows if I could.

Anyhow, I've run into a weird problem and I think it has something to do with the way I have my hard drives set up. My OSes are loaded onto a 40GB drive and I have a 500GB drive with 3 partitions for everything else - one is NTFS, for games installed in Windows, one is FAT32, for all my music and stuff, so I can access it from both Ubuntu and XP and the third one is ext3. That third partition is where I'm installing the game.

I've run the installer from the disc without any problems (I have the original DVD special edition) but every time I try to run the game, from either the command line or from the shortcut it created on my games menu, I get an error about not having the right permissions to run it. I've tried using sudo as well with the same results.

The only thing I can figure is that it has something to do with not being installed to my /home directory (which I don't want to do because one or two games would fill it up). I've made sure that the permissions on the /media/disk directory (where the ext3 partition is mounted) are set to allow this (chmod -R 777 /media/disk) and still can't get it to run.

If it's important, the partitions don't auto-mount when I log in to Ubuntu (is there a way to configure this so it does that doesn't involve editing /etc/fstab?) and I have to access them from 'computer' first.

Up until now I was prepared to say that Feisty is, for all my purposes, far better than Windows XP, but not having partitions auto-mount and having permissions errors when I want to play a game is a big step backwards. :(

So I come here hoping someone might have a suggestion as to what I could try next. Thoughts?

---

### Post by gautada on 2007-10-08
> **deruberhanyok said:**
> I've run the installer from the disc without any problems (I have the original DVD special edition) but every time I try to run the game, from either the command line or from the shortcut it created on my games menu, I get an error about not having the right permissions to run it. I've tried using sudo as well with the same results.

Permissions are not just about access but also making scripts/files executable.  You need to figure out what the script/file you are trying to call and try something like

```
%>sudo chmod +x /path/to/your/file
```

> **deruberhanyok said:**
> The only thing I can figure is that it has something to do with not being installed to my /home directory (which I don't want to do because one or two games would fill it up).

That does not seem right...  It does not really matter.  I had UT installed in /opt

> **deruberhanyok said:**
> I've made sure that the permissions on the /media/disk directory (where the ext3 partition is mounted) are set to allow this (chmod -R 777 /media/disk) and still can't get it to run.

Hmmm... did you run using sudo? what about trying chown?

```
%>sudo chown -R yourusername:users /media/disk
```

> **deruberhanyok said:**
> If it's important, the partitions don't auto-mount when I log in to Ubuntu (is there a way to configure this so it does that doesn't involve editing /etc/fstab?) and I have to access them from 'computer' first.

I can't think of a way to do this via the gui I just edit fstab by hand sorry.

> **deruberhanyok said:**
> Up until now I was prepared to say that Feisty is, for all my purposes, far better than Windows XP, but not having partitions auto-mount and having permissions errors when I want to play a game is a big step backwards. :(

Don't confuse not being able to do something with:
 1.) Not knowing how to do something
 2.) Not wanting to do it they way you are told (fstab)

The power of Ubuntu is not just what you can do but the community.  This is where windows cannot compete.

So I come here hoping someone might have a suggestion as to what I could try next. Thoughts?[/QUOTE]

---

### Post by deruberhanyok on 2007-10-08
Oddly, the files were set to have root as the owner. I didn't have to use sudo to run the installer so I figured it would have made my user name the owner.

I ran the chown command - thanks for that - and it definitely changed the owner to my username. Here's some command line output:

matt@Kismet:/media/disk/ut2004$ ut2004
bash: /usr/local/bin/ut2004: /bin/sh: bad interpreter: Permission denied
matt@Kismet:/media/disk/ut2004$ ./ut2004
bash: ./ut2004: /bin/sh: bad interpreter: Permission denied
matt@Kismet:/media/disk/ut2004$ sudo ./ut2004
sudo: unable to execute ./ut2004: Permission denied
matt@Kismet:/media/disk/ut2004$ sudo sh ut2004
exec: 50: ./ut2004-bin: Permission denied
matt@Kismet:/media/disk/ut2004$ sudo sh System/ut2004-bin 
System/ut2004-bin: 1: Syntax error: "(" unexpected
matt@Kismet:/media/disk/ut2004$ sudo System/ut2004-bin
sudo: unable to execute System/ut2004-bin: Permission denied

I've checked the files and they're all marked as executable and all have my username as the owner. I feel like I'm running up against a wall here.

[i]>>Don't confuse not being able to do something with:
1.) Not knowing how to do something
2.) Not wanting to do it they way you are told (fstab)<<[/i]

I know how to do it. But setting permissions and an 'executable' flag don't seem to work, that's why I'm posting here. Why this would even be necessary if it was installed with my username and not root/sudo seems odd to me.

I find myself hoping that UT3 will include a .deb installer file on the disc. I'd love to see more games with Linux support but having to run an installer from a command line takes me back to the DOS era.

In regards to fstab, I've done it before. Yes, I can edit the file and have the partitions auto-mount. But if I delete one of those partitions or pull the hard drive then I'll run into errors on startup (which, admittedly, I can skip) and I have to go and delete the entry in fstab.

I think a better way to phrase my criticism would have been "I don't understand why this isn't a dynamic system." It seems so outdated compared to the rest of Feisty. It's also the only annoying quirk I've found with Ubuntu in the last six months. It also seems horribly outdated compared to Windows XP, a 6 year old OS, thus my initial statement. Apologies if it ruffled feathers.

---

### Post by Captainm on 2007-10-08
> **deruberhanyok said:**
> Hello Ubuntu gurus,

**The only thing I can figure is that it has something to do with not being installed to my /home directory (which I don't want to do because one or two games would fill it up)**. I've made sure that the permissions on the /media/disk directory (where the ext3 partition is mounted) are set to allow this (chmod -R 777 /media/disk) and still can't get it to run.

If it's important, the partitions don't auto-mount when I log in to Ubuntu (is there a way to configure this so it does that doesn't involve editing /etc/fstab?) and I have to access them from 'computer' first.


This is unrelated to your problem but handy none the less. If you have a big ext3 partition different from the one Ubuntu is installed on it might be a good idea to move your home folder there. 

Here are some easy to follow instructions.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

---

### Post by cogadh on 2007-10-08
+1 on that. I just put Ubuntu on a 120GB drive, with a 20GB partition for the system (way more than it needs), 2 GB for the swap and the remaining 98 GB for the user's home folders. I now have no concerns about running out of space in the home folders, plus if I ever have to re-install Ubuntu, I don't lose any of my personal docs, e-mail, games, bookmarks, etc.

---

### Post by deruberhanyok on 2007-10-09
Hey all, thanks for the tip about the home directory. I thought of doing that when I did the initial install but wasn't sure if I'd be keeping Ubuntu on my system at first so just went with the defaults. I'm planning to do a fresh install with 7.10 - ideally without any dual-booting at all, but I think that depends on Steam compatibility with wine, heh - so I'll likely be doing exactly that.

Also, I tried everything I could think of to get this working and ran into permissions errors every time.

I decided that my initial guess as to the problem was the one thing I hadn't tested, so I created an entry in fstab for the ext3 partition on my big hard drive and ran mount -a to reload everything.

The game now works fine. In fact it seems to run without issue even with compiz fusion running, which surprised the heck out of me.

I still don't understand what is different about having the partition auto-mount with an fstab entry and having it mount only when needed.

Anyhow, if anyone else happens to run into an error like this and your partitions aren't auto-mounting, set up fstab so that the one that contains the game does and hopefully that will fix it.

---

### Post by gautada on 2007-10-09
> **deruberhanyok said:**
> I still don't understand what is different about having the partition auto-mount with an fstab entry and having it mount only when needed.

Probably because it is mounting as root.  Automount makes the device/mount point transparent to the user.

Also, checkout [gparted]("http://packages.ubuntu.com/edgy/gnome/gparted") For a graphical way to adjust the mount table.

---

### Post by deruberhanyok on 2007-10-10
Yeah, I was thinking it would be something like that. It still seems strange that even if it was mounting as root, my username is listed as the owner with all permissions for the files but they still wouldn't launch. Even if I used sudo.

I've used gparted for creating the partitions, changing mount points and so on. I didn't see any settings in the program to enable the auto-mount though, which is why I went to editing fstab.

---

### Post by gautada on 2007-10-10
> **deruberhanyok said:**
> I've used gparted for creating the partitions, changing mount points and so on. I didn't see any settings in the program to enable the auto-mount though, which is why I went to editing fstab.

Ooops sorry I ment to say [pysdm]("http://packages.ubuntu.com/feisty/admin/pysdm")

---

