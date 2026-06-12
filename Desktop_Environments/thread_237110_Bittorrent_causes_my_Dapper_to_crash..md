---
title: "Bittorrent causes my Dapper to crash."
date: 2006-08-15
forum: Desktop Environments
---

### Post by Uentsuru on 2006-08-15
Okay, so just today I was trying to download anime from Bittorrent when suddenly I heard a *click click click* and everything ground to a halt.  The screen froze up and I got several errors on my active torrents (using BitTornado, by the way) regarding an Input/Output error.

I had to cut the power to restart.  After I rebooted, I found that Bittorrent would crash my PC without fail.  I tried downloading one file at a time, I tried to see if it was just one file doing it, I even tried using other Bittorrent programs (KTorrent), but all of them caused sudden computer death syndrome.

If anyone else has had this problem and knows how to overcome it, I would be very appreciative.  And if this is the wrong place to post this problem, I apologize in advance.

---

### Post by n00buntu NJ on 2006-08-15
I haven't had very good success with any linux-native bittorrent clients.  Azureus woulnd't crash my system, but it would render it unusable.  The others I tried had the same effect, plus I just plain didn't like them.  

So I tried to run uTorrent (one of the greatest Windows apps of recent memory - it's tiny - only like 165k), which IMO is one of the best Torrent clients in existence.

It works great, with zero tweaking of wine needed.  Just do:

sudo apt-get update
sudo apt-get install wine
winecfg 

That will get you the latest version of wine, and automatically create the default .wine directory in your /home/username/ folder.  Then all you need to do is download uTorrent from [http://www.utorrent.com](http://www.utorrent.com) and execute it.

You'll obviously need the wine repo, but I don't have it off hand, and I'm late to leave the office, so I'll post it later.

:mrgreen:

---

### Post by Uentsuru on 2006-08-15
It's the strangest thing.  I erased all my torrent files and the respective downloads and uninstalled all my torrent programs.  I then went about fixing my Nvidia drivers.  After that, I reinstalled BitTornado and tried to download Bleach.  So far, I haven't had anymore problems - I wonder if it was a problem with my graphics card...

---

### Post by Uentsuru on 2006-08-18
And it happened again today.  I got an error amongst the lines of "[errno 05]: Input Output error" or something and my computer crashed again.  I fear I may have bad sections of RAM and BitTornado is trying to write onto them.  I checked on the BitTornado forums and there where two posts regarding this, but no replies to either of them (And my attempts to register failed.  I never got the activation e-mail.).

---

