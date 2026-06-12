---
title: "Applications ignoring mime types"
date: 2011-05-24
forum: Desktop Environments
---

### Post by ben2talk on 2011-05-24
Files downloaded with Firefox, Chromium, Miro etc. will not open correctly.

Clicking to open the file (e.g. jpg or ogg) should result in the file opening with eog or audacious.

Results - from Nautilus this works correctly, however from other applications the result is a Nautilus window.

Placing a file 'test.torrent' on the desktop and using terminal to do ```
gnome-open test.torrent
``` or ```
xdg-open test.torrent
``` results in the same behaviour. However, simply clicking the file in Nautilus opens it in Deluge (correct behaviour).

Any ideas how to fix this guys?

---

### Post by Copper Bezel on 2011-05-25
xdg-open merely calls gnome-open. The problem, then, is with gnome-open. I'd initially posted in one of the threads you'd resurrected, but your problem is different from the one explained by the OP there.

Just to further narrow this down:

* Does the Places menu work, or does clicking a location open something other than Nautilus?

* Have you made any major system tweaks lately? Is Gnome the only DE installed?

* Have you tried reinstalling libgnome2-0 (which provides the gnome-open command)?

---

### Post by mc4man on 2011-05-25
You could go take a look at ~/.local/share/applications/mimeapps.list
I'd probably just delete the file and start fresh (especially if you upgraded from 10.10 to 11.04

Then just take one local  ex. each  of the various mimetypes, r.click on > properties > open with > <whatever> to set.

---

### Post by ben2talk on 2011-05-25
First of all I'd like to say thanks for jumping over here and joining my party. I'll do my best to be attentive and hopefully won't end up borking things in the process.

* Does the Places menu work, or does clicking a location open something other than Nautilus?
**Places menu works fine**

* Have you made any major system tweaks lately? Is Gnome the only DE installed?
[B]This issue first appeared after upgrading - and yes, apart from the flakey new environment which preventing me seeing any kind of desktop I have only Gnome installed and run the classic option

I DID open Ubuntu-Tweak, and I'm a little untrustworthy of this software...[/B]

* Have you tried reinstalling libgnome2-0 (which provides the gnome-open command)?[/QUOTE]
**Just now - yes. I was going to purge it, but that would clean out half my system!**

---

### Post by ben2talk on 2011-05-25
I checked this earlier.... 
I did ```
nautilus .local/share/applications/
```
Then I added it as a bookmark, and renamed mimeapps.list to 0000mimeapps.list (zero's put backups at the top of the list for easy restoration).


application/x-bittorrent=deluge.desktop

No problems there... maybe a conflict ensuring that this advice is ignored when opening from a Chrome download window?

---

