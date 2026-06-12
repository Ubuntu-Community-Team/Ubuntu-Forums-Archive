---
title: "Privateer Gold Installation"
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by pofigster on 2007-07-24
Ok, I'm trying to install Privateer Gold Edition.  I downloaded the Linux installation file which is a .bz2.bin.   When it was downloaded I modified permissions and all that good stuff then I tried 

$ sudo sh PrivateerGold1.02a.bz2.bin

The archive integrity checks out good, the decompression of vegastrike space simulator (? I guess Privateer is based on it?)  starts and then after probably a hundred lines of ....... I get:

/home/mark/.setup20193: error while loading shared libraries: libgdk-1.2.so.0: cannot open shared object file: No such file or directory

I check in synaptic for libgdk-1.2.so.0 but didn't see anything like it.  Any pointers? :confused:

---

### Post by Cappy on 2007-07-24
Search on [http://packages.ubuntu.com](http://packages.ubuntu.com)
on the second field for "libgdk-1.2.so.0" and you'll find out you need: libgtk1.2
```
sudo apt-get install libgtk1.2
```
if you're running 32-bit/i386

---

### Post by pofigster on 2007-07-24
Thanks!  I don't know why I didn't think to check the website for the files.

That solved the problem.

---

### Post by Afghan Carl on 2008-06-05
Greetings

I did the same thing when I loaded Privateer Gold but I had some other problems with GTK 1.2.  First, the splash screen for the installation came up normally and you then choose some options.  When I chose an option and clicked "install" it gave me an error message to chose at least one option!  I ran a terminal window and saw that I was getting the following GTK error: 

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkEntry'

Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entry != NULL' failed.

I'm not sure how to fix this and would appreciate any help...  I'm running 8.04 LTS and installed gtk1.2.10-18.1build2...

Also, since Privateer doesn't come up under Synaptic and is in the root directory, what is a good way to remove it if I need to later on?

Cheers,
CK

---

### Post by cisforcojo on 2008-06-22
What gfx card are you using? My install REFUSES to run in fullscreen mode.
I've got an ATI Mobility Radeon X600. It'll work fine in Windowed by complains about an 'xcb lock' problem.

EDIT: This appears to NOT be ATI-specific. My friend who uses NVidia is having the same problem. 

About your removal question, I'd suggest you: Alt-F2 then type 'sudo nautilus' That will allow you to use nautilus as root but definitely BE CAREFUL. Be sure you're deleting the right thing.

---

### Post by alfick3 on 2008-11-24
I didn't seem to have any problems installing it, but when I clicked on the link in the start menu (ok, I know, I'm using a Windows term), I very briefly get a window, and then it disappears.  I've tried running the files from the command promt as well, and just get an error stating the command isn't found.

---

### Post by alfick3 on 2008-12-01
I actually got it working.  Not sure what happened, but I tried again later and it ran for me.

---

