---
title: "Fstab.. i think? auto mounting.."
date: 2007-05-28
forum: Desktop Environments
---

### Post by brandenw on 2007-05-28
I have an hp dv2120us. I have a partition with windows on it, also the default windows recovery partition that HP includes on it from the factory. Ubuntu is now running on a third partition i set up myself. everything works great with the exception of 2 things i would like to modify...

1. Ubuntu is automatically mounting both of the partions, and placing an icon to them on the desktop. It wont let me unmount them. so what do i do? i believe i want to edit /etc/fstab

2. Previously i was a windows only user.. i am learning more about linux, and getting better. i would like to be able to use my music that is in the windows partition. currently since the partition is mounted, i can access it, but i dont want to mount the whole drive, i want to mount just the folder that contains the music.
so the partition is /dev/sda1/
music is stored in the windows installation in C:\Documents and Settings\Branden\My Documents\My Music\

how do i do that?
is it possible to make it read and write? or will it have to be read only?

*this is also probably posted in the wrong section...

thanks for you help

---

### Post by deadguy87 on 2007-06-03
press alt f2 and type gconf-editor that opens up some setting thing on the panel on the left find nautilus then prefrences in there to turn off the desktop icons for them you will still see both of them in computer and places. you'll have to mount the windows partiton completely to get your music. I don't know howto control auto mount yet. I'm kinda new too

---

### Post by vanadium on 2007-06-03
In your first item, it is not fully clear what you finally want. Get rid of the icons? Not automount this partition?

If you want to get rid of the icons, then deadguy already provided an approach. However, the drawback of that approach is that no icons will appear anymore on your desktop, e.g. you might want an icon for a removable USB to appear anyway.

In order to mount your Windows partition without having an icon on the desktop, you can mount it on another location (typically /mnt/ instead of /media). Indeed, all that is mounted inder /media gets an icon on the desktop. Mounting your partition elsewhere involves  editing the /etc/fstab file though.

In order to "selectively" access your music folder, it is very simple. Just create s symbolic link to that folder from somewhere under your home directory. You can do this graphically with Nautilus. Browse to your music folder, right-click and select "Make link". This creates a symbolic link in the current directory, which will be called "Link to My Music". Just move that link under your home directory or in a subdirectory where you find it most convenient to access your music.

Concerning read/write: Linux provides full control for that. However, your Windows partition will probably be formatted in the Microsoft proprietary ntfs format. Until now, Linux could only reliably read it. However, write support is on its way. You need to install the (still experimental) write support using Symantec.

---

