---
title: "HOWTO: Make UT2004 Cross-Platformly Awesome"
date: 2007-08-30
forum: Gaming &amp; Leisure
---

### Post by Akdor 1154 on 2007-08-30
Hey all,

Well, I just installed UT2004, and was reasonably impressed with the fact that it even started (well, after I gave my user account access to its own settings file :-s) and then realized all the fun I'd have to go through installing all the mods and maps I've got under Windows.. well. Let's just say it doesn't have to be that way. :)

My Windows programs are stored on a separate partition, which is my D: drive under Windows, and is mounted as /media/winPrograms. As such, my Windows UT2004 folder is accessed via /media/winPrograms/Games/UT2004. Yours might be somewhere like /media/c/UT2004 for the default, or if Atari has had its nasty way it might me /media/c/Program Files/Atari/UT2004. Anyway, just work out where it is, and remember to "quote" or \escape any paths with spaces.

While I'm by no means an experiences Linux user, I've commented and explained everything in a Lowest Common Denominator fashion, so please don't be offended. :)

[size=4]The Easy Part[/size]
```

# Obviously, if you installed to somewhere else, cd to there instead.
cd /usr/local/games/ut2004

# Backup everything like a good little asexual forum entity.
sudo mv Animations Animations-Linux
sudo mv KarmaData KarmaData-Linux
sudo mv Maps Maps-Linux
sudo mv Music Music-Linux
sudo mv Sounds Sounds-Linux
sudo mv StaticMeshes StaticMeshes-Linux
sudo mv Textures Textures-Linux

# Symlink your Windows directories across (a symlink, created with the console
# program ln, is similar to a Windows shortcut, but so much more useful. There's
# probably more information on the Ubuntu Wiki or your local help files.)
sudo ln -s /media/winPrograms/Games/UT2004/Animations ./Animations
sudo ln -s /media/winPrograms/Games/UT2004/KarmaData ./KarmaData
sudo ln -s /media/winPrograms/Games/UT2004/Maps ./Maps
sudo ln -s /media/winPrograms/Games/UT2004/Music ./Music
sudo ln -s /media/winPrograms/Games/UT2004/Sounds ./Sounds
sudo ln -s /media/winPrograms/Games/UT2004/StaticMeshes ./StaticMeshes
sudo ln -s /media/winPrograms/Games/UT2004/Textures ./Textures

```

That in itself is enough to play any ordinary maps you've downloaded, but if you've got mutators, mods, etc, you'll need to get slightly more complicated...

[size=4]The Slightly More Complicated Part[/size]

What we'll be doing is creating a Union filesystem to keep our two System directories nice and neat. Well, at least nicely synchronized, if not neat. The union filesystem we create is a mechanism to non-destructively and transparently 'merge' two folders into one, so the contents of both are available in a single place. Now, the smarter among you may be thinking "Well, what if both folders have a file called 'xfile' in them?" - don't worry, unionfs allows for this scenario, and one folder is given precendence over the other in case of filename conflicts.

```

# First, we'll need to grab the unionfs tools.
# [Actually I'm not sure if this is required for the purposes here, could an experienced user fill me in on this, please?]
sudo apt-get install unionfs-tools

# If any of the following commands give you some sort
# of 'invalid filesystem type' error, then try rebooting first.

# Now we move our linux System folder somewhere we can find it later:
# (assuming we are still in our Linux UT2004 directory)
sudo mv System System-Linux

# Almost up to mounting our union, but first we need an empty directory for
# where we want to put it:
sudo mkdir System

# This is the fun part: creating the union. Replace any directories with the
# appropriate ones for your system.
sudo mount -t unionfs -o dirs=/usr/local/games/ut2004/System-Linux=rw:/media/winPrograms/Games/UT2004/System none ./System

```
For those interested, here's a breakdown of the command.

The Mount program is, as you may guess, used to 'mount' a filesystem and make it accessible. This program is used when you start your computer, to mount your filesystem root ('/'), your home directory, ('/home'), and possibly your Windows directory ('/media/whatever'), all from different partitions into the same filesystem where you can access them easily.

The -t unionfs option specifies the filesystem type (and the driver/module to use) - in this case it is unionfs, but other types could be ext2 or ext3 (for your Linux partitions), ntfs or ntfs-3g (for Windows NT/2000/XP/etc partitions), and vfat (for FAT and FAT32 filesystems, like you'd find in Windows 95/98/etc, and also most removable devices).

The -o option is for Mount to pass options on to the specific module it's using: in this case, we're telling unionfs the directories we want to make a union from. What we have is a list of directories separated by colons, and a property at the end of each to tell unionfs whether they should be writable (rw), or read-only (ro). It's here that we also get to specify the directory precedence: it's simply in the order you specify directories, from highest to lowest.

The none part is a bit hacky: usually Mount needs a device to mount (generally a partition or removable device, such as /dev/sda1), but in UnionFS's case we've already told it, with the -o dirs= switch. We tell Mount 'none' so it doesn't get cranky at us for telling it something it can't understand.

Lastly, the ./System part simply tells Mount where to put the new filesystem. In this case, it's the System directory of UT2004, so we can finish our nice system integration. :)

If that all works, and UT2004 loads up nicely, you can tell Ubuntu to mount the UT2004 folder each time you boot up.

First, back up the file you're about to edit:
```
sudo cp /etc/fstab /etc/fstab.ut2004backup
```

**For Kubuntu users:**
```
sudo kwrite /etc/fstab
```
**For Ubuntu users:**
```
sudo gedit /etc/fstab
```
(I'm sure users of anything else will be clued-in enough to work out what we're doing here.)

In the editor you've got open, scroll to the **bottom** and add the following as a single line (replacing the directories with your own paths if need be):
```
none	/usr/local/games/ut2004/System unionfs dirs=/usr/local/games/ut2004/System-Linux=rw:/media/winPrograms/Games/UT2004/System=ro
```

Save, and now you're done! :)

-Jarrad Whitaker

---

