---
title: "Link sub-folder to seperate partition"
date: 2006-08-10
forum: Desktop Environments
---

### Post by rhodry on 2006-08-10
I hope I can explain what I want to achieve here without sounding utterly stupid?

I have a large hd on my desktop system. I run Ubuntu 6.06 as my primary os under ext3 filesystem. I have an 80Gb partition that I currently use for loading other os's; for experimenting and learning, etc, etc - currently has latest Mepis on it. Everything important is backed up regularly to external usb drives on a Linksys NSLU2 using 'Simple Backup'.

I have settled on Ubuntu as my os going forward, so the extra stuff is used less and less and I am thinking of dropping the partition size to say 20Gb for os stuff and use the balance as my multimedia (particularly movie) storage area.

I have been trying to learn how to make movies (dvd) from masses of family photos and from tv shows recorded on my digital set-top box. These need to be demuxed, re-created as mpg's and burned to dvd. These files can be quite large and so I thought I would seperate them out from the normal /home stuff. At the same time I thought I might have a look at JFS as a filesystem.

The partitioning & formatting is ok; I know what to do there with QTparted. However, I would like the new partition to still look to Nautilus like it is part of my /home tree structure. So, if I cd to /home/paul/movies (say) it goes and looks at the other partition but still appears in nautilus under /home/paul.

My question is: is this possible?

I would think I would have to adjust my mount parameters in fstab; but can I give the new partition a mount point inside /home? Perhaps I have to mount it quite seperately and create a link of some sort from /home/paul/movies to the new partition?

Any guidance appreciated.

Also, any experience on whether JFS is a good choice for fs when files will tend to be large and may be lots of deleting going on (as I learn software)? :)

Thanks,
Paul.

---

### Post by 23meg on 2006-08-10
> My question is: is this possible?It's possible with a symbolic link. Just go to your home directory and type ```
ln -s PATH
```replacing PATH with the path to your movie storage, which would perhaps be something like /media/h[COLOR="Red"]x[/COLOR][COLOR="Blue"]y[/COLOR]/movies.

---

### Post by maniacmusician on 2006-08-10
or instead of mounting it in media and linking to it, he could probably mount it right in his home folder.

---

### Post by 23meg on 2006-08-10
Sure but keeping it in /media is tidier and sounds more *technically correct*. When mounting drives in home folders there's a certain difficulty faced when one wants to back up the whole home directory (the whole mounted drive gets backed up too unless otherwise specified) and having a separate home partition can complicate things further.

---

### Post by rhodry on 2006-08-10
> **23meg said:**
> Sure but keeping it in /media is tidier and sounds more *technically correct*. When mounting drives in home folders there's a certain difficulty faced when one wants to back up the whole home directory (the whole mounted drive gets backed up too unless otherwise specified) and having a separate home partition can complicate things further.
Thanks folks for confirming I have a number of options. On reflection, I think I will mount it in /media/movies and if I find I REALLY need to see it in my /home structure all the time, I will use the symbolic link.

Thanks again.

---

### Post by Arathon on 2007-12-04
> **23meg said:**
> It's possible with a symbolic link. Just go to your home directory and type ```
ln -s PATH
```replacing PATH with the path to your movie storage, which would perhaps be something like /media/h[COLOR="Red"]x[/COLOR][COLOR="Blue"]y[/COLOR]/movies.
This seems like almost what I want to do, except that it's not working.  I want the Pictures folder under /home/peter to point to /media/sdb3/Pictures, but every time I use "ln -s /media/sdb3/Pictures" or "ln -s /media/sdb3/Pictures Pictures", a symlink called Pictures gets created *underneath* /home/peter/Pictures.  Is there a way around this?

---

### Post by tcommbee on 2007-12-04
make sure you are in your home directory when running the command (not in ~/Pictures)

---

### Post by Arathon on 2007-12-04
> **tcommbee said:**
> make sure you are in your home directory when running the command (not in ~/Pictures)
Yeah, and the correct command is definitely "ln -s /media/sda3/Pictures"; however, running the command just results in the response "ln: creating symbolic link './Pictures' to '/media/sda3/Pictures': File exists".  I'm afraid if I delete the folder itself, the links throughout the GUI won't work anymore, even if I create the symbolic link - for instance, everything in the "Places" menu, and the left-hand navigation bar on all instances of Nautilus.

---

