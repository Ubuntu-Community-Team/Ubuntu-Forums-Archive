---
title: "Deluge crashes with Glib.GError: Unrecognized image file format"
date: 2009-02-07
forum: General Help
---

### Post by chrismja on 2009-02-07
I booted up my laptop today and everything has been running just fine, but when I start deluge, it crashes. If I run it in terminal this is what I get:

Traceback (most recent call last):
  File "/usr/bin/deluge", line 132, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 115, in start_deluge
    interface = deluge.interface.DelugeGTK(config_dir=deluge.common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 80, in __init__
    self.window.set_icon(common.get_logo(48 ))
  File "/var/lib/python-support/python2.5/deluge/common.py", line 154, in get_logo
    size, size)
glib.GError: Unrecognized image file format



Does anyone have any ideas what I need to do? I've uninstalled and reinstalled, but to no avail. I've googled and can't find a fix.

---

### Post by chrismja on 2009-02-08
Anyone have any suggestions? I'd really appreciate it!

---

### Post by brianbrian on 2009-09-24
I too got this error after installing a few programs & updating some libraries.  After doing some googling someone said to change the extension.

1) Make a backup of the file /usr/local/lib/python2.6/dist-packages/deluge-1.1.9-py2.6.egg/deluge/ui/gtkui/common.py

2) sudo gedit common.py  #located in the directory shown above.  

3) The error shows that the program failed at line 57 inside the get_logo section.
Basically the result of the if part will result in two options, deluge.png or deluge.svg  Since the glib failed to use the .svg file I renamed deluge.svg to deluge.png.  This way the program will go for the deluge.png no matter what.  Sure you could probly rewite the whole little section and now have the code decide but I am not a programer yet.

4) Run the program and see if it works, it worked for me.

I hope this works for you.



Taken from common.py

def get_logo(size):
    """Returns a deluge logo pixbuf based on the size parameter."""
    if deluge.common.windows_check():
        return gtk.gdk.pixbuf_new_from_file_at_size(deluge.common.get_pixmap("[COLOR=Lime]deluge.png[/COLOR]"), \
            size, size)
    else:
        return gtk.gdk.pixbuf_new_from_file_at_size(deluge.common.get_pixmap("[COLOR=Red]deluge.svg[/COLOR]"), \
            size, size)

---

### Post by brianbrian on 2009-09-24
After rebooting my computer I see that my machine has a problem with reading .svg files all together.  To solve that problem I compiled librsvg from source and my machine is able to work with .svg files again.  Just to double check, I replaced the edited common.py
back with the original and deluge runs as it should have with it's original code.

You can pick up librsvg over at....
[http://librsvg.sourceforge.net/download/](http://librsvg.sourceforge.net/download/) 

Hope this helps.

---

