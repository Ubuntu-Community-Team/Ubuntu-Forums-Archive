---
title: "ISO creation and mounting?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by crispy_420 on 2006-07-10
This is a three part quest for software.

I know there is probally a tool to do this but I don't know where to start looking. What I want is a CD/DVD copy/burner that I can load a CD into my computer and create an ISO image of it. That way I can make 1:1 copy of disc on a machine with only a single optical drive (laptop & girlfriend's computer). Something like Nero has, an image burner. I may already have the software installed but have not found the solution. I think I just need a nudge in the right direction. :confused: 

On a side note, is there a program to mount those images. I want something with a gui. Something like [Daemon Tools]("http://www.daemon-tools.cc/dtcc/announcements.php") for Windows. 

Also is there anything out there I can use to manipulate the created ISO image? Say take a audio CD's image created and add some other data, images, etc. A believe the closest thing I can think of is [UltraISO]("http://www.ezbsystems.com/ultraiso/index.html").

I have the ability to do this in Windows but the computers I want to do this on aren't running Windows.

---

### Post by kpkeerthi on 2006-07-10
> What I want is a CD/DVD copy/burner that I can load a CD into my computer and create an ISO image of it. That way I can make 1:1 copy of disc on a machine with only a single optical drive (laptop & girlfriend's computer).
Use K3B. I do not have KDE but I found K3B the best for my burning needs.

To mount an iso file:
> 
1. mkdir /media/cdimage
2. mount -o loop <file>.iso /media/cdimage

After you mount the image, you should be able to add/remove files and modify it. Use mount -o rw option.

K3B also supports creatiion of disc images.

---

### Post by crispy_420 on 2006-07-10
I'll give it try tomarrow morning and see if that works. I can swear I tried it before but I'll look again. I'll be back with my results in a few hours.

So is there an option when I select copy a disc?

Thanks for the quick reply.

---

### Post by FredB on 2006-07-10
> **crispy_420 said:**
> This is a three part quest for software.

Right, let's go.

> I know there is probally a tool to do this but I don't know where to start looking. What I want is a CD/DVD copy/burner that I can load a CD into my computer and create an ISO image of it.  
With ubuntu (gnome one), right click on the icon of the click.  After that, choose "copy disc". In the new box, choose "file image" and your iso will be created.

> That way I can make 1:1 copy of disc on a machine with only a single optical drive (laptop & girlfriend's computer).  
No need of 3rd party software for first step.

> Something like Nero has, an image burner. I may already have the software installed but have not found the solution. I think I just need a nudge in the right direction. :confused:  
There is a burn iso option in Nautilus. In "Go" menu.

> On a side note, is there a program to mount those images. I want something with a gui. Something like [Daemon Tools]("http://www.daemon-tools.cc/dtcc/announcements.php") for Windows.  
Erh...


> Also is there anything out there I can use to manipulate the created ISO image? Say take a audio CD's image created and add some other data, images, etc. A believe the closest thing I can think of is [UltraISO]("http://www.ezbsystems.com/ultraiso/index.html").

I have the ability to do this in Windows but the computers I want to do this on aren't running Windows. 
Maybe using K3B or any other burner ?

---

### Post by AZzKikR on 2006-07-10
> **kpkeerthi said:**
> Use K3B. I do not have KDE but I found K3B the best for my burning needs.

To mount an iso file:

After you mount the image, you should be able to add/remove files and modify it. Use mount -o rw option.

K3B also supports creatiion of disc images.

You said mounting an ISO can be done with the following command:

```

mkdir /media/cdimage
mount -o loop <file>.iso /media/cdimage

```

I've read this several times on this forum, and works like a charm. I was wondering however what the option **loop** does. The manpage for **mount** wasn't very helpful, or I may have read past it. Any ideas?

---

### Post by kabus on 2006-07-10
> **AZzKikR said:**
> 
I've read this several times on this forum, and works like a charm. I was wondering however what the option **loop** does.

It tells mount to use a [loop device]("http://en.wikipedia.org/wiki/Loop_device").

---

### Post by crispy_420 on 2006-07-11
That Gnome/right click seems to obvious. Maybe I was looking for the hardway. The main reason for me wanting to add to a disc is so I can add my source.list in there so if I have to do a reinstall. Also maybe add a few other config files (xorg, fstab, etc.). Just a few files to make a reinstall easier.

But thanks guys. That k3b way just got me a folder with all the files in it. I will try these in the am. I'm up too late anyway tonight. Don't want to make too much of a hassle tomarrow.

---

### Post by Thund3rstruck on 2006-07-11
@crispy_420

While they're not gui solutions here are a few very simple scripts you can use:

This script is handy if you burn a lot of CDs 
[Convert Mp3 to Wavs]("http://www.ubuntuforums.org/showthread.php?t=212079")

This script is handy if you mount a lot of isos but don't want
to remember all the syntax
[Simple mountiso script]("http://www.ubuntuforums.org/showthread.php?t=211843")

---

### Post by mcman42 on 2006-07-11
Hm, It would be nice to have something like daemon tools  for .nix but I havent encountered such software yet. However there is a script for nautilus that allows you to right click an iso image and to eiher mount it or unmount. I would recommend to you if you are as lazy as me and tired of typing same commands in terminal every time.

I dont remember th link, but try googling it up with words "nautilus scripts mount iso".

---

### Post by crispy_420 on 2006-07-12
That right click on a mounted CD to copy works like a dream.

mcman42, is this what you were talking about? Here's a few links I found:

[http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/](http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/)

[http://doc.gwos.org/index.php/Mount_ISO_script](http://doc.gwos.org/index.php/Mount_ISO_script)

[http://www.ubuntuforums.org/showthread.php?t=87369](http://www.ubuntuforums.org/showthread.php?t=87369)

[http://g-scripts.sourceforge.net/nautilus-scripts/File%20System%20Management/Mount_Image](http://g-scripts.sourceforge.net/nautilus-scripts/File%20System%20Management/Mount_Image)

But from I saw by just a quick look is unmounting an image is still a hassle. I could be wrong but I'll look tomarrow.

---

