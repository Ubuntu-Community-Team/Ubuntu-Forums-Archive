---
title: "core dump (avant-window-navigator)"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by mevets on 2007-04-06
Avant window navigor crashes everytime it is lauched. I installed the app by downloading the tarball of rpms. From there I converted avant-window-navigator-0.1.1-3.i386.rpm with alien to a deb and installed it. I then go to run the app with 'avant-window-navigator' and I get these results:
```

Segmentation fault (core dumped)

```
when I run avant-preferences i get:
```

/usr/share/avant-window-navigator/window.glade
Traceback (most recent call last):
  File "/usr/bin/avant-preferences", line 250, in <module>
    app = main()
  File "/usr/bin/avant-preferences", line 143, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/bin/avant-preferences", line 221, in setup_chooser
    chooser.set_filename(self.client.get_string(key))
TypeError: GtkFileChooser.set_filename() argument 1 must be string, not None

```
I tried turning beryl off but I still recieve the same error. How can I troubleshoot this problem.

---

### Post by FuturePilot on 2007-04-06
I get the same thing. Every time I try to start it, it gives me segmentation fault core dumped.:confused:

---

### Post by got_nix on 2007-04-07
damn.. no help what so ever huh.. i'm in thee same situation man.. some help here please

---

### Post by mevets on 2007-04-07
I have done some investigating myself. I read:
```
Segmentation fault

... then the program was trying to access a memory location outside its
address space.  The computer detected this problem and sent a signal to your
program, which caused it to abort.

```from [http://web.mit.edu/answers/unix/unix_bus_or_seg.html]("http://web.mit.edu/answers/unix/unix_bus_or_seg.html"), so I thoguht maybe running as root would help. When I ran avant-window-navigator as root I recieved these errors:
```
(process:17833): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:17833): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(process:17833): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault (core dumped)

```
Given this information, can anyone help solve our problems?

---

### Post by FuturePilot on 2007-04-07
Ok I've got it working for me now:)  Here's what I did. I used this guide here [http://ubuntuforums.org/showthread.php?t=351186]("http://ubuntuforums.org/showthread.php?t=351186")
There's a deb on the second page and that's what I used, but you need to do one more thing. Download the source code from the guide and ```
tar -zxvf avant-window-navigator-0.1.1-2.tar.gz 
``` then
```
cd avant-window-navigator-0.1.1/data
``` and here is the important part
```
gconftool-2 --install-schema-file=avant-window-navigator.schemas.in.in 
```

Doesn't work on Dapper but I got it working of Feisty but with some error. But it works.

---

### Post by mevets on 2007-04-07
thanks works !

---

