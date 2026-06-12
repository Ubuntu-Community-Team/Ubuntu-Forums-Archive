---
title: "CGWD Themer Help"
date: 2006-08-18
forum: Desktop Environments
---

### Post by bamf on 2006-08-18
Hey Everybody,

I'm brand new to Ubuntu and Linux and have been messing around with it for about a week...

I just spent the last hour trying to figure out how to get Compiz Themes to work on my notebook. I figured out that I needed the CGWD Themer and found the packages for it and got it. It is now in my System-->Prefrences-->CGWD Themer. So I open it up and there is a huge list of themes and I imported the ones that I had downloaded... but there is no button for the theme to take effect. I try double clicking and doing everything but nothing happens.

> I just found out that its just suppose to change themes when I click on the theme. But Alas, it still does not.

I do have aiglx and compiz installed. Any Help?

-----------------------------

So I thought it might be that Gnome-Decorator was still running so I checked my start up and the compiz startup pointd to /usr/bin/compiz/start, so I looked at that file and it had...

> #! /usr/bin/python

import os
import pygtk
pygtk.require('2.0')

import gtk, gobject
import egg.trayicon

WGII = gtk.Invisible()

def start_compiz():
	global WGII
	WGII.selection_owner_set(atom)
	os.system("killall gnome-window-decorator")
	gobject.spawn_async(['gnome-window-decorator'], \
			     flags=gobject.SPAWN_SEARCH_PATH)
	gobject.spawn_async(['compiz', '--strict-binding', '--indirect-rendering', '--replace', 'gconf'], \
			  flags=gobject.SPAWN_SEARCH_PATH)
	
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
	gobject.spawn_async(['gset-compiz'], flags=gobject.SPAWN_SEARCH_PATH)

def compiz_menu_activate(widget):
	start_compiz()

def metacity_menu_activate(widget):
	global WGII
	WGII.destroy()
	WGII = gtk.Invisible()
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

atom = gtk.gdk.atom_intern("_COMPIZ_GL_INCLUDE_INFERIORS")
	
box.connect("button-press-event", callback)

start_compiz()

gtk.main()


After reading several other posts about this I'm not sure if this is right?

Thanks,
Kiley

---

### Post by DarkAngel88 on 2006-08-20
Same problem here...

---

### Post by jimmygoon on 2006-08-20
If you are using quinn-compiz-aiglx and you have the little red cube icon in your task tray, then right click and choose "Use CGWD".

If not, open a terminal and type:
"cgwd --replace &"

OR type, for possibly better results
"nohup cgwd --replace &"

---

### Post by morphodone on 2006-08-21
> **jimmygoon said:**
> If you are using quinn-compiz-aiglx and you have the little red cube icon in your task tray, then right click and choose "Use CGWD".

If not, open a terminal and type:
"cgwd --replace &"

OR type, for possibly better results
"nohup cgwd --replace &"

thanks

---

### Post by wjoe2003 on 2006-08-24
should I add the "nohup cgwd --replace &" command to the start up program in sessions so my themes will start with compiz?

---

