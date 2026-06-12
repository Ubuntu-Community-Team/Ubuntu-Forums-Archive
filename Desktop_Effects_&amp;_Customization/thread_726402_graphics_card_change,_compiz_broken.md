---
title: "graphics card change, compiz broken"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by dlok on 2008-03-16
Hi all,

I have a ATI Radeon 7500 on my IBM T42, and I was tinkering around with the graphics drivers and xorg.conf to try and get my second monitor working. On a reboot with my TV plugged into VGA out, Gnome complained about not being able to find a suitable graphics card and I had to restart. Now, Compiz does not work. Here are the errors:

$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

** (metacity:5772): WARNING **: Irregular conf file line(1):
# this file contains quirks

** (metacity:5772): WARNING **: Irregular conf file line(1):
# list prgname that need to be ignored below

** (metacity:5772): WARNING **: Irregular conf file line(1):
#

** (metacity:5772): WARNING **: Irregular conf file line(0):

I tried to change back to my old settings, but I stupidly did not save them and am now unsure on what to do. Please let me know if you have any suggestions. (Ideally, I would like to get my graphics card working properly, but just getting Compiz back would be great as well)

Thanks a ton.

---

### Post by dlok on 2008-03-19
Someone please help!

---

### Post by tjvdberg on 2008-04-16
I'm having the similar error messages, but I didn't tinker xorg.conf, and everything seems to work okay. Someone know what these error mean?

outputt "gedit"

```

~$ gedit

** (gedit:6899): WARNING **: Irregular conf file line(1):
# this file contains quirks

** (gedit:6899): WARNING **: Irregular conf file line(1):
# list prgname that need to be ignored below

** (gedit:6899): WARNING **: Irregular conf file line(1):
#

** (gedit:6899): WARNING **: Irregular conf file line(0):


(gedit:6899): Gtk-WARNING **: gnomenu_compatible found at 0xb6b566e0

(gedit:6899): Gtk-WARNING **: gnomenu_menu_bar_class_intern_init found at 0xb6b525e0

(gedit:6899): Gtk-WARNING **: gnomenu_compatible found at 0xb6b566e0

(gedit:6899): Gtk-WARNING **: gnomenu_menu_bar_init found at 0xb6b525a0

(gedit:6899): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed



```

---

### Post by Zorael on 2008-04-16
Mwoah. This doesn't seem to be of the standard mix of error messages. :>

dlok. I suggest you make a backup of your xorg.conf and then reconfigure it.
```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```
If it doesn't work after that we'd need to see the actual contents of the xorg.



tjvdberg. If you create a new user (temporarily, just delete it afterwards if you wish), does the problem occur when logged in to it as well?

Are you using foreign third-party repositories? In other words, are you sure you're not using a version of gedit other than the one available from the official sources?

---

