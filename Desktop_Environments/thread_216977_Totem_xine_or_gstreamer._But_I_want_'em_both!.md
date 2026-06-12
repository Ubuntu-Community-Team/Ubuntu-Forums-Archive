---
title: "Totem: xine or gstreamer. But I want 'em both!"
date: 2006-07-16
forum: Desktop Environments
---

### Post by PryGuy on 2006-07-16
Good day everybody!
I've got a problem here: I've heared that DVD support was exluded from the gstreamer release that was included into Ubuntu 6.06 and it exists in xine only. But! during the installation xine removes totem-gstreamer and I'm not able to watch MPEG4/DivX movies any more.:( 

totem-gstreamer reinstallation removes totem-xine as I expected and DVD menus support disappears.:( Is there any solution to the problem? I really do not feel like installing yet another player for DVDs only but if there's no chance... The situation is rather funny, how Ubuntu team could miss it?

---

### Post by PryGuy on 2006-07-16
Kinda solved it.:) Just installed libxine-extracodecs and it all worked. Will test it out and tell you! Why has the Ubuntu Team replaced gstreamer for xine I wonder?

---

### Post by Hezekiah on 2006-07-16
Gstreamer is, I believe, the upstream default - it's meant to be central to all Gnome-related audio and video work in Gnome apps.  I think this is why it is the default setup.

---

### Post by PryGuy on 2006-07-16
But well, what's wrong with it then?:( 
Really, Dapper seems more buggy than Breezy even though it's really better in it's overall improvements...:(

---

### Post by PryGuy on 2006-07-16
Okay, it appears that we've got xine for Totem and gstreamer for Rythmbox and  all the rest in Dapper. That's how I could configure it at last.

---

### Post by gThree on 2006-07-16
You can keep Totem/g-streamer and run xine with gxine or xine-ui (which I've never tried) as the front end.  Best of both worlds.

I also had to change around my multimedia habits after I upgraded.  Some stuff that used to work didn't ... some stuff that didn't now did.  Breezy a big improvement though overall and between MPlayer, Totem/g-streamer and gxine, I managed to sort everything out.

---

