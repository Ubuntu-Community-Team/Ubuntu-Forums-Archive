---
title: "Avant-preferences?"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by luckyd on 2007-05-28
I just got avant-window-navigator, and when I try to run avant-preferences the output is as follows..
> $ avant-preferences
/usr/local/share/avant-window-navigator/window.glade
(avant-preferences:6005): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 273, in <module>
    app = main()
  File "/usr/local/bin/avant-preferences", line 135, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=I18N_DOMAIN) 
RuntimeError: could not create GladeXML object

I am a complete noob, so any help would be much appreciated:p

---

### Post by Sethalos on 2007-05-28
I tried installing it as well, and I received pretty much the exact same thing:

/usr/local/share/avant-window-navigator/window.glade
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 273, in <module>
    app = main()
  File "/usr/local/bin/avant-preferences", line 158, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/local/bin/avant-preferences", line 240, in setup_chooser
    chooser.set_filename(self.client.get_string(key))
TypeError: GtkFileChooser.set_filename() argument 1 must be string, not None

No idea what to do now.

---

### Post by Sethalos on 2007-05-28
Ok, I fixed it.

I ended up using the command:

sudo apt-get install avant-window-navigator

Once I did that, it showed up in my Accessories folder.

---

### Post by mezcla on 2007-07-17
I'm having the same problem.  i installed from the Pure 64 repository.  here is the error I get:

```
$ avant-preferences
/usr/local/share/avant-window-navigator/window.glade

(avant-preferences:2685): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 267, in <module>
    app = main()
  File "/usr/local/bin/avant-preferences", line 132, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=I18N_DOMAIN) 
RuntimeError: could not create GladeXML object

```

---

