---
title: "gtkEveMon"
date: 2014-05-31
forum: Gaming &amp; Leisure
---

### Post by Moses_Moore on 2014-05-31
Found an old thread for gtkEveMon but it was out-of-date and closed, so I couldn't add newer info.  The listed homepage of [http://gtkevemon.battleclinic.com](http://gtkevemon.battleclinic.com) bounces to a player group's forums, which mention Evemon but not gtkEvemon.

Steps I used for building version 1.9-150:
Go to [https://github.com/gtkevemon/gtkevemon](https://github.com/gtkevemon/gtkevemon) , use the 'Download ZIP' button on the right-side column.
Extract to /tmp/ 
sudo apt-get install build-essential libgtkmm-2.4-dev libxml2-dev libssl-dev
cd /tmp/gtkevemon-master
make
cp src/gtkevemon /usr/local/bin/  # or $HOME/Games/eve/, whatever floats your boat

There's still trouble with the program.  Two things will make it reliably crash:
- Going to menu item "EveMon > Configuration..." will cause it to crash from an unhandled exception.
- Going to menu item "Help > About..." it will eventually segfault & core dump when the request to find the current version times-out (a little over 30 seconds).

---

