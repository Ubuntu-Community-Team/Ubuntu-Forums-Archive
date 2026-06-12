---
title: "cut &amp; copy directories to usb without writing permissions will cause loosing data"
date: 2011-08-03
forum: Desktop Environments
---

### Post by tanoloco on 2011-08-03
Hello,

I'm using lubuntu maverick

```
l:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

I created a folder on my Desktop and wanted to move it on an external usb drive.
To do so I simply used the mouse, right clicked on it and selected "cut" and then I moved to the usb drive, right clicked on it and chose "paste"
Unluckily I hadn't checked the permissions before doing this, and I received the alert of Permission denied because I hadn't write permissions.
There wouldn't be any problem if my folder hasn't disappeared from my Desktop! and there's no way to found it! It's not on my trash and plus I changed rm in the past in order to trash files!
So my folder has simply disappeared!
cut&past hasn't trashed it nor removed it using rm.

I did some tests:
1. only folders disappear while using cut & paste to a usb folder without write permissions. Files are kept.

2. folders disappear on cut & paste to a folder without write permission only if using an external usb destination folder. If you try to cut & paste them to a local folder without write permission (e.g /bin) they are correctly kept after the "permission denied" alert

3. it doesn't matter what kind of usb drive you choose nor what kind of destination filesystem you are using: I tried on a usb drive with a reiserfs partition, and then I tried on a second drive with an ext4 partition. Same result! Folders are gone.

Is this a (known) bug?
Is there any way to prevent this behaviour in the future?
Is there any chance to recover data lost in this way?

Thanks

---

### Post by kansasnoob on 2011-08-03
You confuse me a bit. You said:

[B]I created a folder on my Desktop and wanted to move it on an external usb drive.
To do so I simply used the mouse, right clicked on it and selected "[COLOR="Red"]cut[/COLOR]" and then I moved to the usb drive, right clicked on it and chose "paste"[/B]

But "cut" = delete :o

I haven't used Lubuntu Maverick but I'm now playing with Lubuntu Oneiric testing and **copy-n-paste** seems to work fine (although it does seem slower than nautilus at times).

But cut means CUT, it's not the same as copy!

And nothing in your home folder should normally have special permissions.

---

### Post by tanoloco on 2011-08-03
sorry if I confused you, English is not my mother tongue, as you may notice. :)

I know the difference between cut and copy .. and you are completely right: cut will delete the original item once pasted somewhere else! :) it just moves the item.

My point is when you cut&paste a folder to a place on a usb drive on which you don't have write permission.

I'm using pcmanfm on lubuntu 10.10, but I think there's no difference between ubuntu flavours for that: if you try to cut&paste an item to a folder on which you don't have write permissions (e.g /usr or wherever you can't write) you normally receive an alert with a message saying "permission denied" .. then everything is left as before, I mean the item is left on its original place.
Cut will delete the original item only if moving ends successfully!

What I'm saying is that I noticed that if I cut&paste a folder from whenever (for example my Desktop) to a folder on an external usb drive (for example /media/extusb/jack) on which I don't have write permission this will cause to get the usual message of "permission denied" but then the original folder is not kept as normally! it just disappears.

It's not trashed not removed with rm .. it's simply gone.

So I don't have the moved copy on the targer folder because I don't have write permission on it and of course lubuntu couldn't move it on there.
But I don't have the original copy either because it's been deleted as it has been moved!

This happens only with folders (files work fine) versus an external usb folder (local target folders work fine).
When I say "it works fine" I mean that on cut&pasting I receive the message "permission denied" and the original copy is just kept because it couldn't be moved on a folder without write permission.

Hope it's better explained. :)

---

### Post by phillw on 2011-08-03
> **tanoloco said:**
> .....
My point is when you cut&paste a folder to a place on a usb drive on which you don't have write permission.....


AFAIK, You are relying on the mv command, which is extremely unforgiving. I would really caution about using mv.

Your file 'may' still be there but with prefix **~** so it would be worth doing a find for it.

I can ask the author if he can trap such an error and put the backup switch in which should create a ~file. Such a thing would, realistically, be on the 'wish list' of functionality. Using cp and rm is a safer bet (always have a backup). It would be unlikely to hit before 12.04.

Regards,

Phill.

---

### Post by tanoloco on 2011-08-03
you're right: cp and rm is safer (same as copy&paste and then delete from the gui) than mv (same as cut&paste).
But sometimes I prefer to use mv directly because it's quicker, in particular on large files or folder with huge content.

Thanks for the advice anyway :)

The file is not there with ~ because it wasn't a file, it was a folder.
This strange behaviour only apply on folders.

Anyhow I tried a find on the whole system with the folder name looking on hidden folders too, and nothing went out.

The original folder is just removed.

The strange fact is that this happens only on **folders** and only while cut&pasting on a **usb** destination folder without write permission.

I don't think the author can solve it doing a ~ duplicate, BTW is it possible to create ~ copies of folders too? I think I never seen them.

It looks like the operation over a usb folder return true as the item was correctly moved and so the program continues removing the original item, while it wasn't moved at all.

---

### Post by tanoloco on 2011-08-04
same beahaviour in lubuntu natty:

```
~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

```

1. **create a folder** on your desktop
for example ~/Desktop/test/

2. **mount an external usb** on which there's a folder on which you **don't have write permission**
for example /media/usbdisk/nowrite/ root:root 755

3. cut your folder on the desktop & paste it on the usb folder using the gui,
which simply means:
[INDENT]- right-click on the folder "test" on your desktop and choose "**cu**t"[/INDENT]
[INDENT]- use your filemanager to go to the usb folder and right-click on it and choose "**past**"[/INDENT]

4. A window with the progress bar will open with an error on it saying "test: Error creating directory: **permission denied**"

After that the **original folder** "test" on the desktop [COLOR="Red"]**disappears**[/COLOR], and of course there's no copy on the target folder.
As a consequence [COLOR="Red"]**you loose your original folder and all data in it!**[/COLOR] 
The original folder is removed while the error window is shown, the removing process doesn't wait for the user to press the close button on that window.
So you don't have time enough the create a copy on the fly either while receiving this error, you just loose your data if you do this error.


Using mv from the command line keeps the original:
```
$ cd ~/Desktop
$ mv "test" "/media/usbdisk/nowrite/"
mv: cannot create folder "/media/usbdisk/nowrite/test": Permission denied

```

and the original folder "test" on your desktop is correctly kept.

Thus it's not something about the mv command, but it's something about the gui interaction.
This happens only with cutting folders and pasting them on a usb destination folder on which you don't have write permission.

Is it a bug?

---

### Post by tanoloco on 2011-08-04
Ok, I knew the guilty one!

I started a session on Ubuntu 11.04 and used nautilus to test this strange behaviour, so I could notice that nautilus simply deactivate the command "paste" on the context menu coloring it on dark when you right click on a folder on which you don't have write permission.
So you simply can't go on.

So the "problem" is on pcamanfm, which is the default fm on lubuntu.
In fact I installed it on ubuntu 11.04 and it does the same than on lubuntu as described before, mainly because pcmanfm keeps on showing the "past" command as active even if you right-click on a folder on which you don't have write permission.

I will try to contact the author of pcmanfm.

The version of pcmanfm used on lubuntu natty 11.04 seems to be 0.9.9 from the help > info window of pcmanfm

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
barbara@pc-luca:~$ sudo apt-cache show pcmanfm
Package: pcmanfm
Priority: optional
Section: universe/utils
Installed-Size: 1188
Maintainer: Julien Lavergne <gilir@ubuntu.com>
Original-Maintainer: Debian LXDE Packaging Team <pkg-lxde-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 0.9.8+git-6240436419-0ubuntu1
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfm-gtk0 (>= 0.1.14), libfm0 (>= 0.1.14), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.24.0), libgtk2.0-0 (>= 2.20.0), libpango1.0-0 (>= 1.20.0), libx11-6
Recommends: lxde-icon-theme | gnome-icon-theme, gvfs-backends, gvfs-fuse
Conflicts: pcmanfm-nohal
Filename: pool/universe/p/pcmanfm/pcmanfm_0.9.8+git-6240436419-0ubuntu1_i386.deb
Size: 185422
MD5sum: 84dddb3d3a1dd2ed2edac4d2b64cb592
SHA1: 69bd4b7afd765e41389cb71a82c437eb54270146
SHA256: e1c959ae52e8b46e41a90792a24da1873ad7a80ae4cd90fa09badd2bbe52406b
Description: an extremely fast and lightweight file manager
 PCMan File Manager is a gtk2 based file manager for the X Window System.
 Features:
  * Extremly fast and lightweight
  * Can be started in one second on normal machine
  * Tabbed browsing (similar to Firefox)
  * Drag & Drop support
  * Files can be dragged among tabs
  * Load large directories in reasonable time
  * File association support (Default application)
  * Basic thumbnail support
  * Bookmarks support
  * Handles non-UTF-8 encoded filenames correctly
  * Provide icon view and detailed list view
  * Standard compliant (Follows FreeDesktop.org)
  * Clean and user-friendly interface (GTK+ 2)
  * Support GVFS for auto-mount handling on removable devices
Homepage: http://pcmanfm.sourceforge.net/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

---

### Post by tanoloco on 2011-08-04
As this seems to me a bug of pcmanfm, I opened a new report on launchpad

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/820865](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/820865)

---

