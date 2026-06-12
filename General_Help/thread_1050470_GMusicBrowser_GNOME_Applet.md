---
title: "GMusicBrowser GNOME Applet"
date: 2009-01-25
forum: General Help
---

### Post by aslamp on 2009-01-25
I made a little script with the help of [this]("http://www.pygtk.org/articles/applets_arturogf/"), in python to display the now playing information in the gnome panel as an applet, and in the notification area.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=101029&stc=1&d=1232921273[/IMG]

First of all, you need to download [gmusicbrowser]("http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html"), or use the rep:

```
deb http://squentin.free.fr/gmusicbrowser ./
```

With [this]("http://squentin.free.fr/gmusicbrowser/squentin.key.asc") key.

This script also requires:
[LIST]
[*]**libnet-dbus-perl** (for gmusicbrowser to recognize media buttons)
[*]**xte** (play, forward, back)
[*]**wmctrl** (switching to gmusicbrowser window)
[/LIST]

Then install everything:

```
gksudo apt-get install gmusicbrowser libnet-dbus-perl xte wmctrl
```

Once you have everything installed:
[LIST]
[*]Open up gmusicbrowser
[*]Goto Settings/Plugins
[*]Enable Now playing
[*]Enter this, and replace USER with your user name
```
tee /home/**USER**/.config/gmusicbrowser/nowplaying.info
```
[*]Check "Send Title/Artist/Album in standard output"
[/list]
Now put this code into a file named "gmb.py" in /usr/bin/ (don't forget root), and mark it as executable.

```
#!/usr/bin/env python

# GMusicBrowser GNOME Applet 0.1
# GNOME Applet to display information about gmusicbrowser
# by: Chris Humbert
# GPL

import sys
import pygtk
pygtk.require('2.0')
import gtk
import gobject
import gtk.glade
import gnomeapplet
import gnome.ui
import os
import os.path
import re

class GMusicBrowser:

	def cleanUp(self,event,widget):
		del self.applet
		
	def timeoutCallback(self,event):
		info = self.getInfo()
		self.label.set_markup(" <b>" + 
			self.title + "</b> by <b>" + 
			self.artist + "</b> on <b>" + 
			self.album + "</b> ")
		return 1
            
	def getInfo(self):
		f = open(os.path.expanduser('~/.config/gmusicbrowser/nowplaying.info'),'r')
		self.title = f.readline()[6:-1].replace('&','and')
		self.artist = f.readline()[7:-1].replace('&','and')
		self.album = f.readline()[6:-1].replace('&','and')
		self.length = f.readline()[7:-1]
		self.year = f.readline()[5:-1]
		f.close()		
	        
	def buttonPress(self,widget,event,applet):
		if event.type == gtk.gdk.BUTTON_PRESS and event.button == 3:
			self.createMenu(applet)

	def button(self,icon,button,time):
		if button == 3:
			self.create_menu(icon)

	def aboutInfo(self,event,data=None):
		about = gnome.ui.About("Gmusicbrowser Applet","0.1","GPL",
			"Applet to display current playing track and some functionality",
			["Chris Humbert"],["Chris Humbert"],"Chris Humbert")
		about.show()

	def createMenu(self,applet):
		self.propxml="""
		<popup name="button3">
		<menuitem name="Item 1" verb="GMB" label="View _Gmusicbrowser" 
			pixtype="stock" pixname="gmusicbrowser"/>
		<menuitem name="Item 2" verb="About" label="_About..." 
			pixtype="stock" pixname="gnome-stock-about"/>
		</popup>
		"""
		self.applet.setup_menu(self.propxml,[ 
			( "About", self.about_info ), 
			( "GMB", self.focus ) ],None)

	def play(self,a=0,b=0,c=0):
		os.popen('/usr/bin/xte "key XF86AudioPlay"')
		
	def next(self,a=0,b=0,c=0):
		os.popen('/usr/bin/xte "key XF86AudioNext"')
		
	def prev(self,a=0,b=0,c=0):
		os.popen('/usr/bin/xte "key XF86AudioPrev"')
		
	def focus(self,a,b,c=0):
		info = self.read_proc_info()
		os.popen('wmctrl -a "' + self.artist + '"')

	def __init__(self, applet, iid):
			
		self.timeoutInterval = 500
		
		self.applet = applet
		
		self.hbox = gtk.HBox(homogeneous=False, spacing=0)
		applet.add(self.hbox)
		
		self.evBox = gtk.EventBox()
		self.evBox.connect("button-press-event",self.buttonPress,applet)
		self.hbox.add(self.evBox)
		
		self.label = gtk.Label("Loading...")
		
		self.evBox.add(self.label)
		
		self.nextIcon = gtk.StatusIcon();
		self.nextIcon.set_from_icon_name("media-skip-forward")
		self.nextIcon.set_tooltip("Skip Forward") 
		self.nextIcon.connect("activate",self.next)
		self.nextIcon.connect("popup-menu",self.focus)
		
		self.playIcon = gtk.StatusIcon();
		self.playIcon.set_from_icon_name("media-playback-start")
		self.playIcon.set_tooltip("Pause/Play") 
		self.playIcon.connect("activate",self.play)
		self.playIcon.connect("popup-menu",self.button)
		
		self.prevIcon = gtk.StatusIcon();
		self.prevIcon.set_from_icon_name("media-skip-backward")
		self.prevIcon.set_tooltip("Skip Backward") 
		self.prevIcon.connect("activate",self.prev)
		self.prevIcon.connect("popup-menu",self.focus)
		
		gobject.timeout_add(self.timeoutInterval,self.timeoutCallback, self)
		
		applet.connect("destroy",self.cleanUp,None)
		applet.show_all()
		            
def gmb(applet, iid):
	GMusicBrowser(applet,iid)
	return True

gnomeapplet.bonobo_factory("OAFIID:GNOME_GMusicBrowser_Factory", 
	gnomeapplet.Applet.__gtype__, "hello", "0", gmb)

```

Then make a file called "GNOME_GMusicBrowserApplet.server" and put it in /usr/lib/bonobo/servers/ . Place this in it:

```
<oaf_info>
<oaf_server iid="OAFIID:GNOME_GMusicBrowser_Factory"
            type="exe" location="/usr/bin/gmb.py">

        <oaf_attribute name="repo_ids" type="stringv">
                <item value="IDL:Bonobo/GenericFactory:1.0"/>
                <item value="IDL:Bonobo/Unknown:1.0"/>
        </oaf_attribute>
        <oaf_attribute name="name" type="string" value="GMusicBrowser GNOME Applet"/>
        <oaf_attribute name="description" type="string" value="Control and display info for gmusicbrowser"/>
</oaf_server>

<oaf_server iid="OAFIID:GNOME_GMusicBrowser"
            type="factory" location="OAFIID:GNOME_GMusicBrowser_Factory">

        <oaf_attribute name="repo_ids" type="stringv">
                <item value="IDL:GNOME/Vertigo/PanelAppletShell:1.0"/>
                <item value="IDL:Bonobo/Control:1.0"/>
                <item value="IDL:Bonobo/Unknown:1.0"/>
        </oaf_attribute>
        <oaf_attribute name="name" type="string" value="GMusicBrowser GNOME Applet"/>
        <oaf_attribute name="description" type="string" value="Control and display info for gmusicbrowser"/>
        <oaf_attribute name="panel:category" type="string" value="Utility"/>
        <oaf_attribute name="panel:icon" type="string" value="gmusicbrowser"/>
</oaf_server>
</oaf_info>
```

Then right click on the GNOME panel, and add the GMusicBrowser Applet.

As you can see in the screenshot, it will display "Track by Artist on Album", and put previous, play/pause, and next buttons (hopefully in that order) into the notification area.

Feel free to mess around with the code and play with things. Hope you find it useful as I have!

Chris Humbert

---

### Post by Ivo Moelans on 2010-01-06
That's a nice applet. Have you ever thought of offering it to the author of gmusicbrowser to put on his website? It would be a shame if people didn't find this. :)

On another note: do you know of a way to show the actual volume gmusicbrowser is playing at on the panel in nice big readable numbers?

Anyway, if you have other useful applets/tips like this, I'd like to hear about it. I think gmusicbrowser is totally underrated.

Greetings.

---

