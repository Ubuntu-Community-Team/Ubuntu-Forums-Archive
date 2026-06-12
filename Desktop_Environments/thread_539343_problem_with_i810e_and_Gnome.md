---
title: "problem with i810e and Gnome"
date: 2007-08-31
forum: Desktop Environments
---

### Post by OlympicSoftworks on 2007-08-31
I am having a strange problem with Fiesty.  I run a little non-profit where I take in old computers, install GNU/Linux onto them and either use them to teach GNU/Linux or give them away, so I have installed Ubuntu on many, many computer configurations...this one eludes me however.

The machine booted just fine after the original install, used the 'alternate' cd.  Gnome login came up and went into the desktop as expected...the machine wanted me to update of course so I did.  I rebooted to get the new system level stuff running and that is where I am currently.

I appears that the gnome (gconfd) is having issues.  X runs, the machine is(other then Gnome) running just fine as far as I can tell.  I have sound, networking, and the little proggies I can get to without the menus like screenshot and the right click context menu work fine.  But the gnome toolbars and such are gone.  Just the nice brown Ubuntu wave wallpaper.  The bars were there, in fact they were populated with the default menus and firefox and such...just that it flashed a couple times had some almost visible error windows that almost popped up and then it all went away.

Xorg.0.log of course shows no trouble, but /var/log/messages does.  The following are the entries made as gconf tries to start up the desktop and launcher:

Aug 30 23:19:59 dell866 gconfd (olysoft-5073) starting (version 2.18.0.1), pid 5073 user olysoft
Aug 30 23:19:59 dell866 gconfd (olysoft-5073) resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 30 23:19:59 dell866 gconfd (olysoft-5073) resolved address "xml:readwrite:/home/olysoft/.gconf" to a writable configuration source at position 1
Aug 30 23:19:59 dell866 gconfd (olysoft-5073) resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 30 23:19:59 dell866 gconfd (olysoft-5073) resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 30 23:19:59 dell866 gconfd (olysoft-5073) resolved address "xml:readonly:/etc/gconf/defaults" to a read-only configuration source at position 4
Aug 30 23:19:59 dell866 gconfd (olysoft-5073) resolved address "xml:readwrite:/home/olysoft/.gconf" to a writable configuration source at position 0

As the thing said, the pid is 5073, ps waux | grep gconf shows it is from /usr/lib/libgconf2-4/gconf2 6

If anyone understands what this all is I'd like to know, since I'd like to get this machine working.  It's a nice small mid-speed machine.

Thanks in advance!

---

