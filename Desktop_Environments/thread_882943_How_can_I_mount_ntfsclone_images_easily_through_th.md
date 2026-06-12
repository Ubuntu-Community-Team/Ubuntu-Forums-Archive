---
title: "How can I mount ntfsclone images easily through the GUI?"
date: 2008-08-07
forum: Desktop Environments
---

### Post by DaneM on 2008-08-07
Hello.

I'm spearheading a project at the computer shop that I work at that requires me/the other technicians to be able to clone an NTFS partition into an image file (NOT using the -s option), and mount it using a point-and-click interface.  The problem is that I haven't been able to figure out how to do this, either with or without some serious config file hacking.

Here's how I want the hard drive mounted (WITHOUT editing /etc/fstab):

```

mount -t ntfs-3g /path/to/whatever.img /media/mountpoint -o users,exec,uid=$UID,gid=$GID,allow_others,umask=002

```

This works in the console, if I substitute $SUDO_UID and $SUDO_GID for $UID and $GID respectively, but for some reason, it ignores the users,umask,uid=,gid= options.  (When I look in /etc/mtab or type "mount", it doesn't show them.)  Accordingly, the user that I want to be able to umount the file via point-and-click is unable to do so.  

So far, I've been using a script I made (with the above mount command in it) to mount the image via point-and-click.  This required me to add the following line into /etc/mime.types:

```

application/x-ntfs-image     .img

```

...and add the following into mount-ntfs-img.desktop (put into /usr/share/applications):

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=mount-ntfs-img.desktop
Comment=A BASH script to mount .img ntfs clone files via fuse-mount.
Exec=gksudo /usr/local/sbin/mountfile.sh %f
Icon=gnome-terminal
Terminal=true
StartupNotify=false
MimeType=application/x-ntfs-image;
Type=Application
Categories=GNOME;Core;
OnlyShowIn=GNOME;
Name[en_US]=mount-ntfs-img.desktop

```

I put my script, mountfile.sh into /usr/local/sbin:

```

#!/bin/bash

partpath=$1
part=`echo $partpath | sed -e 's/^.*\///' -`
mountpoint=$part
counter=""

mountit()
{
mount "$partpath" "/media/$mountpoint" -o exec,umask=002,uid=$SUDO_USER,gid=fuse
}

ifvalid()
{
if [ ! -d "/media/$mountpoint" ]
        then mkdir /media/$mountpoint >/dev/null 2>&1
fi

if [ -f /media/$mountpoint/* ]
        then 
        let counter+=1
        mountpoint=`echo $mountpoint | sed -e 's/-[0-9]*//g' -`-$counter
        ifvalid
        else
        mountit
fi
}

ifvalid

if mount | grep "$partpath on /media/$mountpoint" >/dev/null 2>&1
        then
        echo "Your image file ($partpath) is now mounted on /media/$mountpoint."
        read -n 1 -p "Press any key to finish."
fi

```
(Legal stuff: Script is my work, as an employee at PCI Computer Services, and cannot be used for commercial purposes without written permission.  End of legal stuff.)


I then right-clicked on the .img file I wanted to mount and told it to open with mount-ntfs-img.  This mounted it nicely.  Unfortunately, when I go to unmount it by right-clicking on the "partition's" image on the Desktop, it tells me that it's not in /etc/fstab, and that I'm not root, and therefore can't umount it.

I tried going into System -> Authorizations (in GNOME) and giving my user explicit permission to unmount all volumes mounted by other users, but to no avail.

I think I'm going about this the wrong way.  It seems that the Authorizations I gave my user only apply to stuff mounted by HAL or some such, and I don't know how to make that work for me.  Furthermore, I don't know why it's ignoring my various mount options.  So, my question (in a nutshell) is this:

**How can I mount an ntfsclone image (NOT using the -s option) via right-clicking on the .img file in GNOME, and unmount it the same way, as any user?  Even if only the user mounting it can unmount it, that would be fine, so long as I can do so using a point-and-click method.**

PLEASE help me out here!  :-)  I'm really stumped, and my boss is going to start wondering what's taking so long (and I think it would be really cool to know how to do this for my own purposes).

Thanks in advance for any help you are able to render.

--Dane

---

