---
title: "Link a folder from one drive to another folder on another drive"
date: 2008-06-22
forum: Desktop Environments
---

### Post by Jordanwb on 2008-06-22
I'm dual booting XP with Ubuntu so I have the My Documents folder on a 40 GB hard drive (referred to as sda5 in Ubuntu). What I'd like to do is mount the folders like so:

sda5/My Pictures to sdb5/home/jordanwb/Pictures
sda5/My Music to sdb5/home/jordanwb/Music
sda5/My Videos to sdb5/home/jordanwb/Videos
sda5/ to ~/Documents (I think I know how to do this, *)

sda5 uses NTFS

*:
I put

/dev/sda5 /home/jordanwb/Documents ntfs rw

in /etc/fstab, although I think I'm forgetting something.

---

### Post by logos34 on 2008-06-22
you don't need to mount the folders separately--just create soft links in your ~/ (home) directory:
> 
ln [OPTION]... TARGET... DIRECTORY     (3rd form)

**ln -[COLOR="Red"]s[/COLOR] /media/sda5/"My Pictures" Pictures**

etc for the rest

---

### Post by Jordanwb on 2008-06-22
So where would I put that? I want the links to be made on boot. Plus it's a drive located in the /dev folder not /media.

---

### Post by logos34 on 2008-06-22
yes, but where is /dev/sda5 **mounting**?  The usual place is /media

cat /etc/fstab

or 

mount 

cmmand will tell

*just use the 'ln -s' command in the shell (from the /home/user location).  The links will be there from boot up

---

### Post by Jordanwb on 2008-06-22
Okay cool. But I want ~/Pictures to show what's in the My Pictures folder, not a shortcut.

---

### Post by nismoskys on 2009-02-08
> **Jordanwb said:**
> Okay cool. But I want ~/Pictures to show what's in the My Pictures folder, not a shortcut.

^ I second that... is there any way to make a direct link without it showing a folder for a shortcut?

So, to use his example, if you click on ~/Pictures, you immediately see what's in "My Pictures" rather than a link to the folder "My Pictures".

---

### Post by Jordanwb on 2009-02-08
I think you could do something like this:

mount -o bind /path/to/original /path/where/stuff/shows/up

However I'm not sure if this command will work if the original folder is not the root of a file system.

---

### Post by Hobgoblin on 2009-02-08
The problem is you are thinking windows so your logic is all wrong.

/dev/sda5 is a device, you can't directly access this.  You need to mount it somewhere.

You could create a folder /sda5 then mount the device /dev/sda5 to that.  But to save confusion you might be better calling it something else.  Lets put it in /media and call it mywindocs, so the pathname is /media/mywindocs

So...
```

sudo mkdir /media/mywindocs
sudo mount /dev/sda5 /media/mywindocs

```

You'll want to put a line in /etc/fstab to mount this each time you boot [This should help](http://ubuntuforums.org/showthread.php?t=283131).

Then, in your home directory, create links to the folders i.e.
```
ln -s "/media/mywindocs/My Pictures" Pictures
```
(you will probably have to remove the Pictures folder first).  
Filenames with spaces will need quotes around them in Linux.  

This gives you a link which looks like a folder and works like a folder.

---

### Post by Jordanwb on 2009-02-08
Oh screw it a facepalm's not worth it.

I no longer use Ubuntu, I use Gentoo Linux on my computers.

</thread>

---

### Post by nismoskys on 2009-02-10
Thanks Jordanwb, i'll see how that works out.

I think that Hobgoblin is responding to the original (year old) post and not my follow up to the the OP's last post in this thread.

---

