---
title: "New compiz-start.py"
date: 2006-09-20
forum: Desktop Environments
---

### Post by chekolyn on 2006-09-20
Well this is just an updated version of the wonderful [compiz-start.py]("http://www.compiz.net/viewtopic.php?id=1170") script so it works with the new changes for compiz, 2 new programs were introduced: GSM=Compiz Settings Manager and gcompiztheme=CGWD Themer plus they now have their own compiz-start script (I think they had one before, then they took it off and it's back again) with this, changing themes is now posible.

Here's the code, I just hope someone has a use for it ;) .
```

#! /usr/bin/python

import os
import pygtk
pygtk.require('2.0')

import gtk, gobject
import egg.trayicon

def start_compiz():
	gobject.spawn_async(['compiz-start'], flags=gobject.SPAWN_SEARCH_PATH)

def place_menu(menu):
	(width, height) = menu.size_request()
	(menu_xpos, menu_ypos) = tray.window.get_origin()
	menu_xpos = menu_xpos + tray.allocation.x
        menu_ypos = menu_ypos + tray.allocation.y
	if menu_ypos > tray.get_screen().get_height() / 2:
                menu_ypos -= height + 1
        else:
                menu_ypos += tray.allocation.height + 1

        x = menu_xpos;
        y = menu_ypos;
        push_in = True;
	return (x, y, push_in)

def configure_menu_activate(widget):
	gobject.spawn_async(['csm'], flags=gobject.SPAWN_SEARCH_PATH)

def theme_menu_activate(widget):
	gobject.spawn_async(['gcompizthemer', '-i'], flags=gobject.SPAWN_SEARCH_PATH)

def compiz_menu_activate(widget):
	start_compiz()

def metacity_menu_activate(widget):
	os.system("killall gnome-window-decorator")
	gobject.spawn_async(['metacity', '--replace', 'gconf'], \
			     flags=gobject.SPAWN_SEARCH_PATH)


def quit_menu_activate(widget):
	gtk.main_quit()

def callback(widget, ev):
	menu.set_screen(widget.get_screen())
	menu.popup(None, None, place_menu, ev.button, ev.time)

menu = gtk.Menu()
item = gtk.ImageMenuItem(stock_id=gtk.STOCK_PREFERENCES)
item.connect("activate", configure_menu_activate)
menu.append(item)
item = gtk.MenuItem("Themes")
item.connect("activate", theme_menu_activate)
menu.append(item)
item = gtk.SeparatorMenuItem()
menu.append(item)
item = gtk.MenuItem("Restart compiz")
item.connect("activate", compiz_menu_activate)
menu.append(item)
item = gtk.MenuItem("Switch to metacity")
item.connect("activate", metacity_menu_activate)
menu.append(item)
item = gtk.SeparatorMenuItem()
menu.append(item)
item = gtk.ImageMenuItem(stock_id=gtk.STOCK_QUIT)
item.connect("activate", quit_menu_activate)
menu.append(item)
menu.show_all()

tray = egg.trayicon.TrayIcon("TrayIcon")
box = gtk.EventBox()
pixbuf = gtk.gdk.pixbuf_new_from_file("/usr/share/compiz/logo24.png")
image = gtk.Image()
image.set_from_pixbuf(pixbuf)
box.add(image)
tray.add(box)
tray.show_all()
	
box.connect("button-press-event", callback)

start_compiz()

gtk.main()


```

---

