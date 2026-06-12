---
title: "peazip (no such file or directory)"
date: 2009-03-08
forum: General Help
---

### Post by UranUtan on 2009-03-08
Hi,

I would like to install Peazip to handle 7Zip and RAR format ([http://peazip.sourceforge.net/](http://peazip.sourceforge.net/))

As I run Ubuntu 8.10 x64, I used the install instruction recommended by the author:
```
sudo dpkg -i --force-architecture peazip_2.5.1.LINUX.GTK2-2_i386.deb 
```
Then I start the application by the start menu "Applications / System Tools / Peazip". Gnome pops up an error message:

[COLOR="Red"]Could not launch menu item
Failed to execute child process
"peazip" (No such file or directory)
[/COLOR]

What's wrong and how to fix?
Thanks in advance for any help.

---

### Post by dcstar on 2009-03-09
> **UranUtan said:**
> Hi,

I would like to install Peazip to handle 7Zip and RAR format ([http://peazip.sourceforge.net/](http://peazip.sourceforge.net/))

As I run Ubuntu 8.10 x64, I used the install instruction recommended by the author:
```
sudo dpkg -i --force-architecture peazip_2.5.1.LINUX.GTK2-2_i386.deb 
```
Then I start the application by the start menu "Applications / System Tools / Peazip". Gnome pops up an error message:

[COLOR="Red"]Could not launch menu item
Failed to execute child process
"peazip" (No such file or directory)
[/COLOR]

What's wrong and how to fix?
Thanks in advance for any help.

It possibly will not run on a 64 bit platform.

Why not just install the proper packages for 7zip and RAR that are in the repositories?

---

