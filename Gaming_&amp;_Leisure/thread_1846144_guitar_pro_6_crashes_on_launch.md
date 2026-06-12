---
title: "guitar pro 6 crashes on launch"
date: 2011-09-18
forum: Gaming &amp; Leisure
---

### Post by jerguy1928 on 2011-09-18
I recently downloaded guitar pro 6 for linux and activated it. My computer is 64-bit but i am using 32 bit wrappers. When i try to launch guitar pro 6 form the applications menu, it shows the banner for one second and then it crashes.However, when using the XFCE desktop environment, it works just fine. how do i fix this problem?

---

### Post by An Sanct on 2011-09-18
Welcome!

For a start, run the application from terminal and go through the output, you can also post it here, so we will be able to see what the problem is.

---

### Post by jerguy1928 on 2011-09-18
It got a little farther than last time, it started to play the start up sound, but still crashed. anyway the output is:

```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:27389): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:27389): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:27389): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:27389): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:27389): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:27389): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:27389): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:27389): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:27389): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:27389): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(<unknown>:27389): Gtk-WARNING **: Error loading theme icon 'dialog-question' for stock: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: wrong ELF class: ELFCLASS64

(<unknown>:27389): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:27389): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(<unknown>:27389): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(<unknown>:27389): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(<unknown>:27389): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(<unknown>:27389): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed
Segmentation fault
```

---

### Post by An Sanct on 2011-09-19
Are you using Natty - 11.04 or Oneiric - 11.10?

If so, maybe try switching to a 2D desktop.

---

### Post by jerguy1928 on 2011-09-19
> **An Sanct said:**
> Are you using Natty - 11.04 or Oneiric - 11.10?

If so, maybe try switching to a 2D desktop.
I'm using Natty, and could you clarify what you mean by switching to a 2-d desktop.

---

### Post by An Sanct on 2011-09-20
At the point when you log in, you can choose "Unity" or "Classic desktop" (gnome).

There where a lot of changes with Unity, the desktop manager...

Here is also a [forum post]("http://forum.ubuntu-fr.org/viewtopic.php?id=469621") (french), with people having the same problem as you and [google translated to english]("http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D469621")

Well to get to the core of the problem, the ELFCLASS64 mentions, that the application is having trouble finding the proper 32bit libraries it needs (GP6 is i386!) and in the guitar-pro forum I found, that a workaround would be to add *gksudo* to the launcher, thus making it sudo... IMHO it would be better to fix the paths so, that it has access to the proper ai32bit libs without administrative privileges. [link to the forum]("http://getsatisfaction.guitar-pro.com/arobas_music/topics/after_ubuntu_11_04_upgrade_i_cant_open_gp6")

---

### Post by Elfy on 2011-09-20
Thread moved to Gaming & Leisure.

---

### Post by HuaiDan on 2011-09-20
Just my 2 cents:
As a workaround, you can always use tuxguitar, which I personally have found to be a satisfactory replacement for Guitar Pro.

In terminal:

sudo apt-get install tuxguitar

---

### Post by FelipeAF on 2011-10-12
Hi, I had the same problem with ubuntu 11.10. I found a workaround:
deb -x [Guitar pro 6 deb file].deb gp6dir
cd gp6dir/opt
gksudo. / Guitarpro

I do not know why, but there is no need to use gksudo or program crashes

if libs are missing, download the file from gp6libs.tar.gz [http://www.box.net/shared/g9oxbvqq6y](http://www.box.net/shared/g9oxbvqq6y) folder and unzip the executable guitar pro

---

### Post by Finn bjerke on 2011-10-20
I installed guitar pro under Ubuntu 10.10 it works except import functions. Under 11.10 its not working at all, installing the deb files leads nowhere, so I now use dual boot. Dual boot is using Ubuntu 10.10 and 11.10 on same harddrive no problem, reboottime is 25 secunds. I can live with that. 
 
For import I use tuxguitar batch conversion, you can convert any file (almost) to guitar pro 5 file (.gp5) 
 
Guitar pro is not very "pro" imho. I cant believe I paid 59 usd for it. I wrote about it in a different thread called dual boot guitar pro solution or something go search

---

### Post by satanselbow on 2011-10-20
> **HuaiDan said:**
>  
sudo apt-get install tuxguitar
 
+1 for tuxguitar.
 
I still gp5 on my win partition but it rarely gets used - it very much depends on exactly what you are using gp6 for but, to me, it has the feel of a "new version because we haven't bought one out in a while" release rather than actually bring any worthy new features or stability :( Bling interface and b***er all else.

---

### Post by Finn bjerke on 2011-10-29
A bit of tinkering and a new guitar pro 6.1 solved the problem, it worx very well now. I use Ubuntu 11.10 32 bits and install according to guitar pro homepage procedures.  BTW password is NOT the guitar pro password but the password you use for Ubuntu. 

THis programme is much better than tuxguitar, but it does not import other file formats as it should. You can use tuxguitar for batch file conversion, converting a lot of files takes you 2 minutes.

If Ubuntu 64 bits is a problem, you might consider using dual boot and a 32 bit version for guitar pro.

---

### Post by Finn bjerke on 2011-10-31
The programme works well on new laptop on the old PC its not installing. Strange, outdated hardware maybe ??  The PC is 6 yrs old.

---

### Post by Finn bjerke on 2011-11-09
It seems that libss something is missing so try this: 


So here is how you do it in Ubuntu 11.10 
Install Guitarpro 6.1 

In case its not loading  when you click the icon

Install synaptic from the software center 
From synaptic install libssl.so.0.9.8  
Enter password etc.  (dont forget: password is not your guitar pro password but your Ubuntu password)  install soundbanks form the internet (2 gig!)

---

### Post by ZliS on 2012-05-23
Ubuntu Studio 12.04 x86
I have an error and crash of the Guitar pro 6.1
```
Object::connect: No such signal PlaySettingsWidget::tuningChanged() in /home/build-linux/BuildMachine/workspace/gp/Sources/GuitarPro/widgets/UniverseSubWidget.cpp:133
Object::connect: No such signal BankListWidget::tuningChanged() in /home/build-linux/BuildMachine/workspace/gp/Sources/GuitarPro/widgets/UniverseSubWidget.cpp:133
Object::connect:  (sender name:   'SearchTreeWidget')
Object::connect: No such signal QWidget::tuningChanged() in /home/build-linux/BuildMachine/workspace/gp/Sources/GuitarPro/widgets/UniverseSubWidget.cpp:133
Object::connect:  (sender name:   'TrackMidiProperties')

(process:14128): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.1/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:14128): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.32.1/./gobject/gtype.c:2722: You forgot to call g_type_init()

(process:14128): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(process:14128): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:14128): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:14128): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(process:14128): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
&#1054;&#1096;&#1080;&#1073;&#1082;&#1072; &#1089;&#1077;&#1075;&#1084;&#1077;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1080;&#1103; (core dumped)

```
Does anybody know anything about that?

---

