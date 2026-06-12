---
title: "Nautilus Folder Icons and Emblems Not being remembered"
date: 2010-09-15
forum: Desktop Environments
---

### Post by alanrodas on 2010-09-15
Hello all.
I have a little big problem with my Nautilus.

I've recently acquire a new HDD and I've decided to use it for multimedia files.
So I've edited my fstab so it mounts this disk at startup.

What's more important, I've bind the folders in that disk (i.e. media/theDisk/Music) to a folder in my home directory (i.e. /home/me/Music) so I can have all the folder mounted at home (Mount the disk in /home/user is not possible because Nautilus start to whim about not being able to set some files in .nautilus or something, I believe its because it does not know which disk to save to or something like that)

So everything works fine, except for folder icons. When I open the home directory, all folders in the disk are shown with the Desktop default icon. Even if I change them (whether from home or from the mounted disk) the next time I open the home directory they are shown with the Desktop icon. Emblems are lost too.

I don't seem to be able to find a way to solve this so I ask for help.

Any ideas?

Thanks in advance

P.S. Sorry for my bad English

---

### Post by TwelveGauge on 2010-09-15
what's the full error message?

---

### Post by alanrodas on 2010-09-15
There is no error message.
Its not an error per se, but a weird thing that should not happen.

The icons I set are being rememberd for the folders I bind.

I try to make an example

I have bind /media/multimedia/music to /home/myuser/music in the fstab by the following line

/media/multimedia/music /home/myuser/music none bind

I have changed the icon of the /media/multimedia/music folder to be /usr/share/icons/Humanity/64/folder-music.svg

When I open /home/user the icon of music is desktop.svg instead of the one I've chocen.

If I open /media/multimedia the icon of music is folder-music.svg

If I change the icon in /home/myuser/music to folder-music.svg It changes but when I close the folder the changes are lost.

If I open /home/myuser and then go to music and back to /home/myuser by pressing up, then the icon of music is effectively folder-music.


What I want is a way of opening /home/myuser and see the icons I've chosen for the folders Ive binded. But I cant figure out a way of doing this because Nautilus doesn't automatically searches the icons I chose unless I open the folder and then go up.

Does anyone run into something similar?

Maybe I'm the only one binding folders from another partition and trying to set icons to them.
The reason of using binds instead of symbolic links is that I don't want that folders to be accidentally deleted nor the little arrow that is shown for the symbolic links. Maybe theres a way to make the link not deletable (I guess that's just a permissions stuff) and not show the arrow in the icon. If there is, then that's good to.

Thanks

---

### Post by Cherry Cotton on 2011-02-05
I’ve had this problem for the past year and a half, and it’s really been bothering me too...

I have my whole home folder on its own partition (mounted to “/home/tina”), so that might be relevant. But, I’ve always had my home folder on its own partition, even before I had this problem.

Oh, I want help... :(

---

### Post by Cherry Cotton on 2011-02-05
Okay, I found a solution: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/405432](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/405432)

Delete the entire contents of “$HOME/.local/share/gvfs-metadata”. That might do the trick. For me, the folder just seemed to contain cached information about optical discs I’d inserted, but no file or folder metadata. It looks like the problem began for me when file/folder metadata started being stored in .local/share/gvfs-metadata instead of .nautilus/metafiles (about a year and a half ago, according to file-modified dates, so I guess that was Ubuntu 9.10).

Of course, you might want to back up that folder in case it does contain anything important. I don’t think it did for me, though.

---

