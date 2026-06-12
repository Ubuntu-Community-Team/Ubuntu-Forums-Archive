---
title: "Things to consider before removing windows"
date: 2008-12-16
forum: General Help
---

### Post by happinesskills on 2008-12-16
I currently have a Dual-boot with Windows Vista & Ubuntu Hardy. I want to get rid of my Vista partition & just have Ubuntu, but I can never get up the courage (if that's what you'd call it) to get rid of it. Here's what I currently have set up.

Vista
 - taking up space (60GB)
 - has a few viruses & is pretty much screwed
 - this partition has all my stuff on it
 - haven't used it since I install XP into VirtualBox

Ubuntu
 - Partition only has 8GB on hard drive (because GPaprted won't let me resize Vista (NTFS) down to it's 60GB
 - Using it all the time
 - Have installed pretty much all I need

PS: I have already backed up all the files I can think of to an External Hard Drive

---

### Post by p0op on 2008-12-16
I was in the same boat as you also. The only way to to get your mind set to realize you don't need windows anymore is to just do it. That's what I did, and I have absolutely no regrets. Just back up the things you want, and make the move. :)

---

### Post by northern lights on 2008-12-16
If you have a VBOX or VM with XP setup, that should indeed do the job whenever you feel like indulging in old habits.
If all the data is backed up you can simply format the Vista partition from within Ubuntu.

Nonetheless, I personally don't like having just one OS installed and always keep a fallback system. You could make that another instance of (K)Ubuntu, Debian. You could venture into the other world and go for RedHat or SuSE (not my choice). I use Arch. Anyhow, it doesn't really matter, but I'd keep a fallback.

---

### Post by Liviu-Theodor on 2008-12-16
So if you already made a good backup, you can worry no more.

You should be careful about these:
1. use gPartEd to change the partition layout on your system.
2. maybe you will need a bigger swap partiton (or maybe you don't).
3. to have the new partition(s) enabled when loggin in, you should run in a terminal:
```
blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
At the last command use the new values found with the first command.
4. Now edit the file [FONT="Courier New"]/boot/grub/menu.lst[/FONT] (maybe you need superuser rights to do that). Remove any Windows reference from it.

If you change your mind, and want to install Vista again, and want to keep your ubuntu installation, see the [http://ubuntuforums.org/showthread.php?t=993805]("http://ubuntuforums.org/showthread.php?t=993805") thread.

---

### Post by Arup on 2008-12-16
Get it out, I did last year, stopped dual booting as I realized I had no need for Windows anymore. I don't do games so there is nothing apart from games that Ubuntu cant' do. Of course, mindset needs to be changed, when we switch from Windows to Mac, we never complain, we adjust, exactly same attitude is needed here.

---

### Post by happinesskills on 2008-12-16
Allright. I'm ready to get rid of it (Thank God!!)

Just one thing before I do. I there anything I need to do, or do I just press delete? (see my screenshot for what's there)

---

