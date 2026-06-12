---
title: "Collection of 27 free games for Linux (and Windows and OSX)"
date: 2007-06-10
forum: Gaming &amp; Leisure
---

### Post by Golyadkin on 2007-06-10
Also btw, I have loads of fun playing these brainteasers: 

[http://www.chiark.greenend.org.uk/~sgtatham/puzzles/](http://www.chiark.greenend.org.uk/~sgtatham/puzzles/)

These are 27 free puzzle games which run on pretty much any computer, even if it is from the stone age. Games don't have to use 64 vertex shaders and 128 pixel pipelines to be a fun distraction :)

They are released by Simon Tatham, the great man who blessed us with PuTTY :)

---

### Post by Golyadkin on 2007-06-10
To install this package, just run: 

> sudo apt-get install sgt-puzzles

---

### Post by Golyadkin on 2007-06-10
With this script you can show all of the puzzles and launch them with buttons:

> 
#!/usr/bin/python
import gtk, sys, os

try:
  fp = open("/var/lib/dpkg/info/sgt-puzzles.list")
except:
  print "sgt-puzzles not installed!"
  sys.exit()

games = [
  os.path.split(x.strip())[1]
  for x in fp if x.startswith('/usr/games/')
]
games.sort()

def startgame(event, gamename):
  os.system("/usr/games/"+gamename+" &")
  gtk.main_quit()

win = gtk.Window()
hbox = gtk.HBox()
vbox1 = gtk.VBox()
vbox2 = gtk.VBox()
win.add(hbox)
hbox.add(vbox1)
hbox.add(vbox2)
count = 0
for g in games:
  count += 1
  b = gtk.Button(g)
  b.connect("clicked", startgame, g)
  if count % 2 == 1:
    vbox1.add(b)
  else:
    vbox2.add(b)

win.connect("destroy", gtk.main_quit)
win.show_all()

gtk.main()


Save this as ** /usr/local/games/sgt-index** ,  chmod +x it, and add it to the menu. 

Script was written by [this person.]("http://www.kryogenix.org/days/2006/08/14/simon-tathams-portable-puzzle-collection-launcher")

---

### Post by mali2297 on 2007-11-28
It's a very nice collection of puzzles. :KS

---

### Post by matthewcraig on 2007-11-28
Can we get these into a Debian package and so people can use Synaptic to access them?

---

### Post by mali2297 on 2007-11-29
> **matthewcraig said:**
> Can we get these into a Debian package and so people can use Synaptic to access them?

There is already a package in the universe repository: [sgt-puzzles]("http://packages.ubuntu.com/gutsy/games/sgt-puzzles").

I chose to compile the games myself though, since I didn't want the gnome-dependencies.

---

