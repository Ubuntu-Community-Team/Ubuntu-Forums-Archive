---
title: "I've managed to break my desktop"
date: 2010-02-18
forum: Desktop Environments
---

### Post by Alf Stockton on 2010-02-18
On my Karmic system I have broken my desktop, by I think, deleting the folder ~/Desktop because it was empty.
Even though I have recreated the ~/Desktop it still looks like:-
[IMG]http://www.stockton.co.za/Screenshot1.png[/IMG]
I really do not want to see all those icons plastered all over my background image.
Please tell me how I fix this.

---

### Post by amsterdamharu on 2010-02-18
Yes, I wouldn't want to work with a desktop like that. Horrible those dogs.

You might want less icons on your desktop as well.

Anyway the folder desktop might be mounted on home or something, can you give the following commands in the terminal and post the output?

```
cd ~
mount
more Desktop/

```

---

### Post by Alf Stockton on 2010-02-18
> **amsterdamharu said:**
> Yes, I wouldn't want to work with a desktop like that. Horrible those dogs.

You might want less icons on your desktop as well.

Anyway the folder desktop might be mounted on home or something, can you give the following commands in the terminal and post the output?

```


cd ~
mount
more Desktop/

```

alf@alf-laptop:~$ cd ~
alf@alf-laptop:~$ mount
/dev/sda2 on / type ext2 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alf/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alf)
alf@alf-laptop:~$ more Desktop/

*** Desktop/: directory ***

Does the above mean anything to you?

---

### Post by Alf Stockton on 2010-02-18
BTW The dogs look a lot better without the icons.....:D

---

### Post by TheNessus on 2010-02-18
your Desktop wasn't empty, it had hidden files. you need those back.

---

### Post by Alf Stockton on 2010-02-18
That is annoying. Where would I find them? Can they be found ? or would rmdir have cleared them as well as getting rid of the folder?

---

### Post by TheNessus on 2010-02-18
> **Alf Stockton said:**
> That is annoying. Where would I find them? Can they be found ? or would rmdir have cleared them as well as getting rid of the folder?

it's not a big of a problem. got a live cd? the Desktop of the OS on the live cd would have these files. Or just anyone with Gnome...
by the way, I am purely guessing, since I have not used Gnome in a while and cannot check. 

Another way to safely fallback on, is to run the pure-gnome command (google it), it would re-install all the packages. Might remove some KDE/XFCE packages though... but I'm not sure it'll help.

You might actually want to check config editor (alt-f2 then config editor, or config-editor, dunno) and check if Nautilus shows your desktop properly, there might be a broken link somewhere over there.

---

### Post by amsterdamharu on 2010-02-18
No, on hardy I tried to see what happens when renaming Desktop.
on Hardy
Not logged in as anyone pressed control + alt + F1
logged in as root and renamed the Desktop folder:
```
mv /home/my_user/Desktop /home/my_user/orgdesktop
```
pressed control + alt + F7 and logged in as my_user, sure enough my home folder shows up on the desktop no I logged out and pressed control + alt + F1 and issued the following command:
```
mv /home/my_user/orgdesktop /home/my_user/Desktop
```
Then control + alt + F7 and logged in as my_user, strange enough the home folder still shows, rebooted doesn't solve it either (yea I come from Windows). I am owner of the Desktop folder and have full rights on it.

If I look in the Desktop directory it has no hidden files in there. Somehow so settings file got screwed and did not unscrew when the Desktop folder returned.

---

### Post by wojox on 2010-02-18
Open a terminal and copy and paste this:

```
gksudo gedit /.config/user-dirs.dirs
```

Fix this:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

### Post by Alf Stockton on 2010-02-18
On my Karmic system that does not work as there is no /.config

sudo ls -al /.config/user-dirs.dirs
ls: cannot access /.config/user-dirs.dirs: No such file or directory

---

### Post by wojox on 2010-02-18
Can you go into Places > Home Folder and Ctrl+H and look for .config/user-dirs.dirs and edit it?

---

### Post by amsterdamharu on 2010-02-18
Thanks, could not find that file tried to with find but it lists too many.
```
find . -type f -mtime 0
```I know it should be something in home folder so listed it from there. To edit that file you don't need to be su the .config directory is in your home dir so you can press alt + F2 and type
```
gedit ~/.config/user-dirs.dirs
```Thanks again that worked and luckily no dogs on my desktop only some strange looking bird.


Got the find command, next time something goes wrong I'll check the files coming out out of this command:

> find . -type f -mmin -100

That is the last 100 minutes, if the system worked fine 15 minutes ago it can be reduced to 15

---

