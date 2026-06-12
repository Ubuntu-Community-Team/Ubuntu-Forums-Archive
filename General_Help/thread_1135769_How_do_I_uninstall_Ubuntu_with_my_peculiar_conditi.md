---
title: "How do I uninstall Ubuntu with my peculiar conditions?"
date: 2009-04-24
forum: General Help
---

### Post by piovertwo on 2009-04-24
This computer is a dual-boot system with Windows Vista Home Premium and Ubuntu 8.04. I installed Ubuntu by following this: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm). I want to remove the Ubuntu partition and give its space back to Vista.

I've been poking around the web on how to uninstall. They mostly gave the same answers. But, I have some problems which wouldn't make me able to follow other websites' instructions. That's when you guys come in.

Here are my problems:
1. I don't have my Ubuntu Live CD.
2. I don't have a Vista CD because this OS is built-in.
But those are moot points, because
3. My DVD drive doesn't work!

Now, how do I uninstall Ubuntu with those weird conditions of mine?

Thank you so much for being able to help.

---

### Post by paradigm2 on 2009-04-24
> **piovertwo said:**
> This computer is a dual-boot system with Windows Vista Home Premium and Ubuntu 8.04. I installed Ubuntu by following this: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm). I want to remove the Ubuntu partition and give its space back to Vista.

I've been poking around the web on how to uninstall. They mostly gave the same answers. But, I have some problems which wouldn't make me able to follow other websites' instructions. That's when you guys come in.

Here are my problems:
1. I don't have my Ubuntu Live CD.
2. I don't have a Vista CD because this OS is built-in.
But those are moot points, because
3. My DVD drive doesn't work!

Now, how do I uninstall Ubuntu with those weird conditions of mine?

Thank you so much for being able to help.

Some people might see this as being mean, but:

You probably need to go to a windows forum or other windows related resource.

It's just the facts.  You want to keep windows as your main partition, not ubuntu (which you want erased).  We're not windows experts and might not be familiar with exactly what you need to do (You've said it yourself, your conditions are peculiar) and all the particulars involved with windows vista.  And if you don't have a backup or windows vista installation disk, that makes it even riskier...

You need to keep windows working and need help with modifying the mbr (master boot record) and the boot sector and all of this.  And you need info specific to windows...

Good luck.

---

### Post by bacardiandwatermelon on 2009-04-24
From memory, if you did a wubi install from vista.. Isn't there an option to uninstall it from programs in the control panel?

Otherwise just remove grub by following these instructions...

[http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12]("http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12")

Then delete the linux partition from the vista partition manager...

---

### Post by piovertwo on 2009-04-25
Thank you guys for pitching in.

And, yes. I may have to refer this to a Windows forum.

Will simply deleting and deactivating GRUB before the partition work? I've been thinking about it. But I'm not too sure.

_New Question:_
I still want to keep Ubuntu, but I want to downsize its partition and give some back to my Windows partition. This is alongside upgrading to 9.04. Can I do that?

Because if I can, I wouldn't have to delete Ubuntu at all.

---

### Post by spiderbatdad on 2009-04-25
If you are currently running Intrepid Ibex, you can upgrade with the command ```
sudo update-manager -d
```Then select the offered distribution upgrade. I would wait several days before try this method, The servers a usually under very high load after a new release, so your upgrade could take much much longer.

It used to be fairly common practice to burn a gparted lice cd and use it for resizing partitions. I have not heard much talk about it for a while, but I have used the gparted disk in the past and it worked like a charm.

[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

lol. meant gparted live, not super grub...all the talk about mbr got me mixed up...edited above anr replaced super grub with gparted.

---

### Post by -kg- on 2009-04-25
I don't know about partitioning with SuperGRUB, but there's another one called [the GPartEd Live CD]("http://gparted.sourceforge.net/") that is specifically set up for partitioning operations.

Of course, all of this may be moot, since piovertwo has stated his DVD drive doesn't work.  Does it just not work under Ubuntu, or in Windows, as well?  You might need to go get another one and install it.  They're cheap these days...$15 or $20.

---

### Post by xyzt on 2009-04-25
> **piovertwo said:**
> Thank you guys for pitching in.
Will simply deleting and deactivating GRUB before the partition work? I've been thinking about it. But I'm not too sure.

_New Question:_
I still want to keep Ubuntu, but I want to downsize its partition and give some back to my Windows partition. This is alongside upgrading to 9.04. Can I do that?

Because if I can, I wouldn't have to delete Ubuntu at all.

Ah! Well, [COLOR="Red"]if you remove GRUB you will have no more boot at all.[/COLOR] That means no system at all. Zilch.

Removing GRUB from a dual boot with Vista is trickier than just using a boot device and MS-DOS [FONT="Fixedsys"]fdisk /mbr[/FONT] to rebuild the boot sector.

If you just want to resize the partitions, Vista has a decent partition manager (somewhere in disk management?) or you can use [FONT="Fixedsys"]parted[/FONT] or [FONT="Fixedsys"]gparted[/FONT] in Ubuntu.

You can also do that, if you're installing 9.04 fresh, during the disk partition management which occurs during installation.

---

### Post by piovertwo on 2009-04-25
Will simply resizing the Ubuntu partition not hurt it? Like, let's say, from 35 GB I make it 20 GB. Would that work fine?

---

### Post by spiderbatdad on 2009-04-25
should be fine.

---

### Post by arashiko28 on 2009-04-25
Just curious, why are you deleting an OS that actually works and keeping the biggest failure of all times as your OS?

Since it's an embedded OS, must have a restore option, one that allows you to return to factory settings, mine had it, just save all your data because it may wipe it down and go to the restoring software and choose factory settings, this will return your vista to the day you bought it.

---

### Post by piovertwo on 2009-04-25
No, I decided not to delete it at all. :) I went back to use it again and I remembered how much I *love* Ubuntu.

My ultimate question:
Now, what I want to know is how to downsize the partition. Plus, what is the most hassle-free way to upgrade from 8.04 to 9.04? Is it worth upgrading?

---

### Post by jimbob on 2009-04-25
You can shrink the Ubuntu partition but it will lob it off the back end, not the front so Vista won't be able to expand into the new space because it won't be contiguous.  If you can shrink Ubuntu to a little less than half its current size, then you can create a new partition at the end and move it to there.  Then delete the original partition and expand Vista into that space.

PS:  It's always worth upgrading IMHO.

---

### Post by piovertwo on 2009-04-25
Using what? Would GParted do nice?

---

### Post by jimbob on 2009-04-25
Very nice.  That's what I use all the time.  Make yourself a stand-alone bootable copy on CD when you get the chance.
   [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by piovertwo on 2009-04-25
How can I apply your first piece of advice in using GParted?

---

### Post by jimbob on 2009-04-25
Right now you're kind of screwed because you don't have a CD/DVD drive.
If I were you I would either a) Get yourself a drive/burner from your local 
computer parts store (they are dirt cheap now - I just bought one from Newegg 2 weeks ago for $21. and free shipping) or b) Grab a friend and talk them into burning Gparted Live CD iso on their computer.

Scratch (b) until you get a drive (I'm losing my mind here).
 Maybe try to borrow a drive from someone??

---

### Post by compgeek83 on 2009-04-25
basics of it are you really need an optical drive, from there you can try some of the things listed above but.... they are all risky given that you dont have a Vista CD.

The secret about the Vista CD problem is that you CAN borrow one from someone else and use it to reload your computer if necessary.  This is legal as long as you use the license code (product key) stuck to the side/bottom of YOUR computer.  Unlike windows xp home/pro/media center, Vista installs from a DVD, and this DVD contains all 4 versions of Vista, the product key you use determines which features are "activated", they are all there actually, just wont show up until you pay for them so to speak.

---

### Post by hatalar205 on 2009-04-25
> **jimbob said:**
> Right now you're kind of screwed because you don't have a CD/DVD drive.
If I were you I would either a) Get yourself a drive/burner from your local 
computer parts store (they are dirt cheap now - I just bought one from Newegg 2 weeks ago for $21. and free shipping) or b) Grab a friend and talk them into burning Gparted Live CD iso on their computer.

Scratch (b) until you get a drive (I'm losing my mind here).
 Maybe try to borrow a drive from someone??

If you have a USB stick you needn't buy a new CD/DVD Drive. Save your money. Just follow the following link.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
(Don't forget to format it before extracting and copying files into the USB stick.)
I have been installing many distros in this way. And it is **faster than a CD or DVD drive** while installing and booting.

---

### Post by -kg- on 2009-04-25
> If you have a USB stick you needn't buy a new CD/DVD Drive. Save your money. Just follow the following link.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
(Don't forget to format it before extracting and copying files into the USB stick.)
I have been installing many distros in this way. And it is faster than a CD or DVD drive while installing and booting.

Still, as I've said before, these days a computer without a CD/DVD burner is severely limited.  There are so many things you can use a burner for, and frankly, I wouldn't be without one.  As cheap as they are, I would still advise buying one and installing it.

I don't know how easy or hard unetbootin is to implement, but nearly everyone can burn an .iso to disk and boot to it.  Also, we can only assume that he is able to boot to a USB device.  I have a reasonably new desktop that can't, but is still capable of running Vista.

---

