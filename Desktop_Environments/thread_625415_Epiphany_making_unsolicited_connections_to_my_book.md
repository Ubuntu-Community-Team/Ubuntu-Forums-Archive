---
title: "Epiphany making unsolicited connections to my bookmarked sites?"
date: 2007-11-27
forum: Desktop Environments
---

### Post by yeow on 2007-11-27
I noticed that 1-2min after Epiphany startup, its cookies list (emptied last session, including clearing history & cache) will contain cookies from a few of my bookmarked sites, all this when Epiphany is left alone & not moved from my homepage.

Prior to noticing this odd behaviour, I had enabled its "Favicon Fallback" extension, and was visiting all my bookmarked sites to load their favicons. Not too sure abt this, but seems like a majority of my "unsolicited cookies" are from those sites without favicons on my bookmarks list.

Another problem: one of those sites had a problem with its Security Certificate, and Epiphany kept bugging me abt it (that's what alerted me to the problem - Security Certificate warning from another site while Epiphany still at homepage). After many times, I finally told Epiphany to "always trust" the Certificate. Now I can't seem to undo this. Using "Certificate Manager", when I try to delete the Certificate, the "OK" & "Cancel" buttons don't work.

Thanks for any help & suggestions.

---

### Post by yeow on 2007-11-28
Opps, I forgot these other details:
- Ubuntu Gutsy
- Epiphany 2.20.1 (installed from Synaptic a day ago)
- "Only from sites you visit" is my cookies setting

---

### Post by yeow on 2007-11-28
-Deleted, see new post below-

---

### Post by yeow on 2007-11-28
OK, I restored an earlier image of Ubuntu prior to this problem, and found it does NOT happen with default Epiphany. But it happens because of either "**Auto Reload Tab**" or/and "**Favicon Fallback**" extensions. What I did to get the problem:

1. Enable "Auto Reload Tab" & "Favicon Falllback" extensions

2. Go to these 3 example webpages (safe), then Add Bookmarks for them:
[WhatIsMyIP.com]("http://www.whatismyip.com/")
[A Geek To Live article on SystemRescueCD]("http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php")
[SecureIX]("https://www.secureix.com/config.shtml")  <- has problem with website's Security Certificate

3. Visit the webpages again via Bookmarks.

4. Clear browser cache ("Temporary Files"), clear history, delete all cookies. Then close Epiphany.

5. Start Epiphany, then open Personal Data cookies window (empty with blank homepage)

6. Click on Bookmarks toolbar to see drop-down list, or open Bookmarks window  <- this triggers the odd behaviour

=> I will see "Connect to untrusted site" alert for SecureIX
=> I will see cookies for lifehacker.com and whatismyip.com added to my Personal Data cookies window
=> Disabling "Auto Reload Tab" & "Favicon Falllback" extensions at this point will not help

[[IMG]http://img264.imageshack.us/img264/946/screenshot001km1.th.png[/IMG]](http://img264.imageshack.us/my.php?image=screenshot001km1.png)

[[IMG]http://img255.imageshack.us/img255/1674/screenshot002ei4.th.png[/IMG]](http://img255.imageshack.us/my.php?image=screenshot002ei4.png)

---

### Post by seanf on 2008-02-18
Try deleting the contents of ~/.gnome2/epiphany/favicon_cache - seems to have worked for me.

---

