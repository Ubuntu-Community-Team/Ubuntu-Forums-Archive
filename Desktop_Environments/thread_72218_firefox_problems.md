---
title: "firefox problems"
date: 2005-10-05
forum: Desktop Environments
---

### Post by davie on 2005-10-05
Hello all. I know nothing, so please forgive me.
My problem is that I can't launch mozilla-firefox. The modem I use is configured ok because I can use icq and email. 
The trouble seemed to start after I tried to install a recommended upgrade through the software update manager. 
When the problem persisted I tried to use 'sudo apt-get install mozilla-firefox' in root and got the following:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
latex-xft-fonts xprt-xprintorg
The following packages will be upgraded:
mozilla-firefox
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/8802kB of archives.
After unpacking 24.6MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 61381 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.6-1ubuntu1~5.04ubp1
(using .../mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error
processing 
/var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb (--unpack):
trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic',
which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Anyone any idea how to proceed? Thanks very much.

---

### Post by Ampersand on 2005-10-05
It looks like the problem is from the 'mozilla-firefox' package being replaced by 'firefox'.

Does it work if you try running 'firefox' instead of 'mozilla-firefox'?

---

### Post by firecat53 on 2005-10-05
There was an issue with the 1.0.7 upgrade. There are numerous threads posted already with fixes for this problem. Good luck!

Scott

---

### Post by davie on 2005-10-06
[QUOTE=firecat53]There was an issue with the 1.0.7 upgrade. There are numerous threads posted already with fixes for this problem. Good luck!
Scott[/QUOTE]

Thanks Scott. Apologies. I did do a quick search before I posted, but I'll have a proper look now. 
All the best,
Davie

---

### Post by Gárgula on 2005-10-06
When I install this package my firefox stop work.

--
(Gecko:10247): Gtk-CRITICAL **: gtk_widget_get_parent_window: assertion `GTK_IS_WIDGET (widget)' failed

(Gecko:10247): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `src != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(Gecko:10247): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(Gecko:10247): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:10247): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

Falha de segmentação

--

Any idea? :confused:

---

