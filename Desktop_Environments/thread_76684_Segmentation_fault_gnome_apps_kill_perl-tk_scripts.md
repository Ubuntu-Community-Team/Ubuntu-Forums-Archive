---
title: "Segmentation fault: gnome apps kill perl-tk scripts"
date: 2005-10-15
forum: Desktop Environments
---

### Post by dakine_1111 on 2005-10-15
I think there is something wrong with perl-tk, gtk or both in Breezy.
4 machines:

3 upgraded from hoary to breezy
1 updated from breezy rc1 to breezy final

When I start: 

widget 

(or an other perl-tk script) and then open a gnome app, for example:

gnome-about

widget closes with a segmentation fault

If I start multiple perl-tk scripts - all running perl scripts will be killed by the gnome application!

The last output of:

strace widget

read(4, "\241 \3\2\22\0`\0036\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(4, "\20\0\7\0\22\0`\3_MOTIF_WM_MESSAGES\35\0", 28) = 28
read(4, "\1\34\4\2\0\0\0\0\317\1\0\0\0\0\0\0\34\0\0\0\34\0\0\0\n"..., 32) = 32
write(4, "\21\0\2\0006\1\0\0", 8)       = 8
read(4, "\1\0\5\2\5\0\0\0\24\0\0\0\1\0\0\0\0\0\0\0\10\0\0\0\10\0"..., 32) = 32
readv(4, [{"_GTK_LOAD_ICONTHEMES", 20}, {"", 0}], 2) = 20
select(5, [4], [], [], NULL)            = 1 (in [4])
ioctl(4, FIONREAD, [32])                = 0
read(4, "\241 \5\2\1\0`\0036\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

I'm able to reproduce this an all 4 machines.

Can someone confirm this behavior?

cssh user@192.168.177.89

fails with:

Cannot open pipe for writing: Keine Kind-Prozesse at /usr/bin/cssh line 643.

(cssh is a perl script from clusterssh)

Since Breezy I get lots of warnings when I start synaptic in a gnome-terminal:

(synaptic:11201): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:11201): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: assertion `src != NULL' failed

(synaptic:11201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: assertion `src != NULL' failed

(synaptic:11201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: assertion `src != NULL' failed

(synaptic:11201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: assertion `src != NULL' failed

(synaptic:11201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_data: assertion `width > 0' failed

(synaptic:11201): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: assertion `src != NULL' failed

(synaptic:11201): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

By the way - when I switch to tty1 login as user and start

mc 

or 

aptitude 

the menu looks very broken.

Does anybody, maybe with a fresh Breezy installation has the same problems?

---

### Post by reedlaw on 2005-11-16
I am having problems with cssh too.  Whenever I run it I don't get the window in which commands are entered.  Even with only one server selected the small command box crashes.  I don't get any errors there, but I sometimes get this:
```
Cannot open pipe for writing: Interrupted system call at /usr/bin/cssh line 643.
```

---

### Post by dakine_1111 on 2005-11-17
A small workaround is to edit /etc/csshrc

```
terminal=/usr/bin/xterm
```

This works until you start a gnome app -> Segmentation fault :confused:

---

### Post by reedlaw on 2005-11-30
Thanks, that works!  
I do notice that a gnome apps kills the cssh box though.  I tried opening Abiword after cssh and the command box closed but the terminals were still opened.  Has anyone found a solution yet?

---

### Post by sterni1971 on 2005-12-21
i stiil see the same problem. the workaround
do it for me and is okay for the thinks i want do.

---

### Post by Martin-Herrmann on 2006-05-02
Hi,

yes, I can confirm this behavior on two different machines both with Ubuntu 5.10 and only the packages installed needed to install Perl-Tk 804.027 (make, libx11-dev, gcc, build-essential, libncourses5-dev and libstdc++6-dev).

A Perl/Tk application (here Mapivi [http://mapivi.de.vu]("http://mapivi.de.vu")) closes with a segmentation fault when a gnome application is started. The start of other applications also causes a segmentation fault, but some others are OK, e.g. there is no crash when starting a xterm.

This is very annoying!
Any ideas or even solutions?

Regards, Martin

---

### Post by Martin-Herrmann on 2006-06-01
I found a solution for this problem here:
[https://launchpad.net/distros/ubuntu/+source/perl/+bug/27261](https://launchpad.net/distros/ubuntu/+source/perl/+bug/27261)

It's a 3 line patch to one of the Perl/Tk files (tkEvent.c).
After appling the patch I complied Perl/Tk again and now my Perl/Tk apps including Mapivi run stable! Yippee!!!

Here is what I entered to compile Perl-Tk 804.027:
make clean
perl Makefile.PL
make
make test
sudo make install

Regards, Martin

---

