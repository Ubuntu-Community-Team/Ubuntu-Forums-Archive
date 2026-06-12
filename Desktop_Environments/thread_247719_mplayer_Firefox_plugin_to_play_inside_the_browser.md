---
title: "mplayer Firefox plugin to play inside the browser?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by linhgb on 2006-08-31
Hi all,

I'm trying to figure out how to get mplayer to play embeded movies inside the Firefox window instead of a popup. I've checked out the config site: [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)

and I've put 

noembed=0
fileonly-embed=0

in /etc/mplayerplug-in.conf, ~/.mplayer/mplayerplug-in.conf and ~/.mozilla/mplayerplug-in.conf

but it doesn't seem to have any effect. Searching the forums only got me solutions to the opposite way (getting Mplayer to popup) and most of those threads were from the Hoary era. 

Any tips? Thanks a lot.

---

### Post by louis_nichols on 2006-08-31
The easiest way is to install package mozilla-mplayer from the repos. It does everything for you.

---

### Post by linhgb on 2006-08-31
That's the same package I installed, but media content still play in a popup window instead of inside the browser.

---

### Post by linhgb on 2006-08-31
This is interesting. On my new (just set up last night) machine with Kubuntu 6.06, it works as intended, but on my old machine with Ubuntu 6.06 upgraded all the way from Hoary, it doesn't get embeded inside the browser. I'll see if I can figure this out. :)

---

