---
title: "GTK2+ apps look ugly in Kubuntu"
date: 2007-03-31
forum: Desktop Environments
---

### Post by Zeroangel on 2007-03-31
I am having problems with GTK2 apps under Kubuntu Edgy. I want them to look like the QT theme. I've installed gtk2-engines-qt but unfortunately it tends to flake out sometimes and instead of using my QT colors, the engine will use an ugly darker shade of grey.

Additionally I will get the errors similar to the following, from GTK2 apps when I run them from the console.
```
(<unknown>:22440): Gtk-CRITICAL **: gtk_text_buffer_insert: assertion `gtk_text_iter_get_buffer (iter) == buffer' failed

(<unknown>:22440): Gtk-CRITICAL **: gtk_text_buffer_insert: assertion `text != NULL' failed

(<unknown>:22440): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
```
The errors differ from program to program but they tend to mention gdk_pixbuf_whatever assertions failing a lot.

FYI: GTK style is QT and my QT style is QtCurve. I am using the proprietary 'official' NVIDIA drivers, as well as beryl-manager (running kwin most of the time).

---

### Post by Zeroangel on 2007-03-31
NEVERMIND!

I solved the problem by using this command to search for 'gdk'```
apt-cache search --names-only gdk
```

and finally this to reinstall it```
sudo dpkg-reconfigure gdk-imlib11
```

Restarted X -- BAM! Mission accomplished (I think).

---

### Post by luisromangz on 2007-03-31
Don't use Qt style, use QtCurve instead. You can find it in [http://www.kde-look.org]("http://www.kde-look.org"). Since I use it, my desktop apps looks almost exactly the same (but for some icons) whether they are qt apps or gtk apps.

Try it!

---

