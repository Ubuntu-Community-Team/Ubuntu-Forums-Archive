---
title: "Gnusticker its there, but not working..."
date: 2006-03-20
forum: Desktop Environments
---

### Post by davidfield on 2006-03-20
So there i am getting all excited because after using so many HOWTO's on this page, i thought i would have a go at writing my own.. I used to use KDE, and like the knewsticker and wanted something the same for gnome, so i found GNUSticker.

the reason i want something in the ticker bar, is just basically because it is a more immediate delivery of news to my desktop.. If i have to keep opening RSSOwl, Liferea or even anything under firefox (straw i think it was) I just get off track and never get round to reading any news.. so if its ticking in the gnome-panel i can see whats going on without actually opening anything..

I digress..

So i read the readme, and got all the dependencies for python loaded as requested via apt-get/synaptic

- Python 2.3 or greater ([http://www.python.org/](http://www.python.org/))
- Boost python libraries ([http://www.boost.org](http://www.boost.org))
- PyGTK  2.4.0 or greater ([http://www.pygtk.org/](http://www.pygtk.org/))
- gtkmm 2.4.8 ([http://www.gtkmm.org/](http://www.gtkmm.org/))
- gthread-2.0 ([http://www.gtk.org/](http://www.gtk.org/))

After haing a problem with the ./configure i found out i needed

libgtk2.0-dev libgtop2-dev python-gtk2-dev

then everything configured, made and sudo made installed no problems,, did a killall gnome-panel nothing in the add panel option, so i did what all good people do, i went ot hier webpage..

[http://gnusticker.sourceforge.net/](http://gnusticker.sourceforge.net/)

and at the bottom of that page it says use ./configure --prefix=/usr 

so make claen, and restart

all went ok..

killall gnome-panel and there we go an Gnusticker icon, so i clicked on add..

Nothing..

Back to the webpage, which reads..

> NOTES
Since it is a bonobo component, you must ensure that the .server file it is installed on a path reacheable by bonobo activation server. (for example: for Fedora distribuition, the installation path should be set as follow: ./configure --prefix=/usr ). Otherwise you must properly set the BONOBO_ACTIVATION_PATH to [your choosen prefix]/lib/bonobo/servers in you ~/.bash_profile file

Had a look in Synaptic and there was loads of Bonobo stuff NOT installed, so i installed it.. and still nowt..

i would still like to write a howto on installing this app, does anyone have any idea why this may not be working?

---

### Post by chaumurky on 2006-04-21
I have gotten as far as you and have the same problem. The .server file is in the same place as the others and ownershop and permissions are the same as well. I don't think anything else is required so it's a complete mystery as to why it isn't working. i wonder where any debug info can be accessed...

---

