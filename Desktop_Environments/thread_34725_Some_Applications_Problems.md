---
title: "Some Applications Problems"
date: 2005-05-16
forum: Desktop Environments
---

### Post by Sniffer on 2005-05-16
Ok, let's start with :) 

**1st -** I can't make mplayer embebbed with Firefox, i have installed mplayer plugin but it seems only to work with mozilla browser...but have no result with Firefox....

Any solution..can i add mplayer to mozplugger??


**2nd -** After ripping to ogg my CD with Sound Juicer, how can i apply vorbisgain to a lot of files instead of one by one..

ex: vorbisgain file.ogg


**3rd - ** There is anyway that i can change the encoder (ex: oggenc, lame 3.90.3) in Sound Juicer or i have to use the default ones?

Thks in advance for the help

Sniff.

---

### Post by Maestro23 on 2005-05-16
[QUOTE=Sniffer]Ok, let's start with :) 

**1st -** I can't make mplayer embebbed with Firefox, i have installed mplayer plugin but it seems only to work with mozilla browser...but have no result with Firefox....

Any solution..can i add mplayer to mozplugger??


**2nd -** After ripping to ogg my CD with Sound Juicer, how can i apply vorbisgain to a lot of files instead of one by one..

ex: vorbisgain file.ogg


**3rd - ** There is anyway that i can change the encoder (ex: oggenc, lame 3.90.3) in Sound Juicer or i have to use the default ones?

Thks in advance for the help

Sniff.[/QUOTE]


Question #1:  Did you install both following the Ubuntu Guide? [http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

---

### Post by daenney on 2005-05-16
[QUOTE=Maestro23]Question #1:  Did you install both following the Ubuntu Guide? [http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)[/QUOTE]
 About that Ubuntu guide; MPlayer has some broken dependencies because it will never install over here...
I use the nl.archive mirrors and have added those merin-ftp ones to to apt, do I need to add the backports too to get the necessary files and install mplayer once and for all?

---

### Post by Maestro23 on 2005-05-16
[QUOTE=daenney]About that Ubuntu guide; MPlayer has some broken dependencies because it will never install over here...
I use the nl.archive mirrors and have added those merin-ftp ones to to apt, do I need to add the backports too to get the necessary files and install mplayer once and for all?[/QUOTE]

Hmm.. I followed the guide and added all the extra repositories like it said.  Have had no probs with Mplayer or the plugin for Firefox.  I would say yes, add all extra repositories, and see what happens.

---

### Post by Sniffer on 2005-05-16
[QUOTE=daenney]About that Ubuntu guide; MPlayer has some broken dependencies because it will never install over here...
I use the nl.archive mirrors and have added those merin-ftp ones to to apt, do I need to add the backports too to get the necessary files and install mplayer once and for all?[/QUOTE]


No i haven't follow that guide just because it was crashing when playing DVD and it was to slow when starting.

I have compiled mplayer from the source instead and that solve my problems.. the only thing i miss now is the integration with Firefox. :-|

---

### Post by Sniffer on 2005-05-16
[QUOTE=Maestro23]Hmm.. I followed the guide and added all the extra repositories like it said.  Have had no probs with Mplayer or the plugin for Firefox.  I would say yes, add all extra repositories, and see what happens.[/QUOTE]


Ok, will add nerim to the Rep and use his deb mplayer plugin package instead...hope it works   :-# 


Any help on my sound juicer questions will be good also  :wink: 

Hope i'm not asking too muchhhhhh  :grin:

---

### Post by Maestro23 on 2005-05-16
[QUOTE=Sniffer]Ok, will add nerim to the Rep and use his deb mplayer plugin package instead...hope it works   :-# 


Any help on my sound juicer questions will be good also  :wink: 

Hope i'm not asking too muchhhhhh  :grin:[/QUOTE]

If that .deb pkg doesn't work, I have used this in the past when I have compiled from source on mplayer in other distro's of linux.  Just d/l the source tarball and follow the step-by-step install instructions on the page and you should be fine.  Good luck man..

Plugin Link: [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

---

