---
title: "Trouble making applet. Hope you guys can help."
date: 2011-02-25
forum: Desktop Environments
---

### Post by quality_sam on 2011-02-25
Hi Guys, I'm trying to write my first python applet. Now i can make an applet  they displays text, or a pythin program that access a config file. But  the moment i do both, the applet displays only a single white pixel on  the taskbar. Code is below. If i leave like this, it displays text. If i uncomment  the comented lines, it displays a pixel. With run-in-window parameter it  runs fine. Does anyone have any ideas please? I'm stumped.
  **!/usr/bin/env python**

  import pygtk import sys pygtk.require('2.0')
  import gnomeapplet import gtk
  def factory(applet, iid):
  # import ConfigParser
# config = ConfigParser.ConfigParser()
# config.read('usage.cfg')
# done=str(config.get('main', 'used'))
done="65Gb" 
label = gtk.Label(done)
applet.add(label)
applet.show_all()
return gtk.TRUE
 def showAboutDialog(*arguments, **keywords):
  pass
 if len(sys.argv) == 2:
  if sys.argv[1] == "run-in-window":
    mainWindow = gtk.Window(gtk.WINDOW_TOPLEVEL)
    mainWindow.set_title("Ubuntu System Panel")
    mainWindow.connect("destroy", gtk.main_quit)
    applet = gnomeapplet.Applet()
    factory(applet, None)
    applet.reparent(mainWindow)
    mainWindow.show_all()
    gtk.main()
    sys.exit()
 if **name** == '**main**':
  print "Starting factory"
gnomeapplet.bonobo_factory("OAFIID:GNOME_usage", gnomeapplet.Applet.__gtype__, "Simple gnome applet example", "1.0", factory)

---

