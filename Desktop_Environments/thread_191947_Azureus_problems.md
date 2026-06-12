---
title: "Azureus problems"
date: 2006-06-08
forum: Desktop Environments
---

### Post by WebDrake on 2006-06-08
There appear to be some serious issues with the Azureus package available via Synaptic.

The issue with not having an icon in the system tray (or rather, having a blank icon that in Gnome is just 1 pixel wide) has already been mentioned elsewhere.

Today, I downloaded a .torrent file to my desktop and, on opening it with Azureus, got the following error message:

[list][i]Not a File0PILOTNot a File0-Not a File0CASANot a File0NONot a File0VOXNot a File0--Not a File0JamendoNot a File0-Not a File0OGGNot a File0VorbisNot a File0q8Not a File0-Not a File02005.07.15Not a File0%5Bwww.jamendo.com%5D.torrent' could not be opened:

Not a File[/i][/list]

Another popup box suggested, *Ensure sufficient temporary file space available (check browser cache usage)*.

I'm buggered if I know what this can be.  There's over 12 GB free in my /home partition, and the fact that there are other problems leads me to suspect it's just the package that's broken.

Any ideas?

---

### Post by DeadEyes on 2006-06-08
I tried Azureus and quickly uninstalled it after 5 minutes. It would pop up an error message in the bottom right of the screen(zordered on top of everything including the workspace switcher).
When I clicked the hide button the window stayed.
Exiting Azureus left it there.
Running xkill did nothing.
Ended up logging out to get rid of it.

Needless to say first impressions last and I won't be trying it again.

---

### Post by WebDrake on 2006-06-08
[QUOTE=DeadEyes]Needless to say first impressions last and I won't be trying it again.[/QUOTE]
This is an overreaction.  Azureus is a great program but this version of it is broken.

Incidentally is there something wrong with the various Ubuntu torrents?  I was just trying to download Xubuntu to check it out, and KTorrent reports that it is "stalled".

And ... does someone know how to check, in KTorrent, that NAT/firewall/router issues are sorted?  Azureus was claiming a DHT error earlier but I'm not sure I trust that package.

---

### Post by zba78 on 2006-06-08
[QUOTE=WebDrake]There appear to be some serious issues with the Azureus package available via Synaptic.

The issue with not having an icon in the system tray (or rather, having a blank icon that in Gnome is just 1 pixel wide) has already been mentioned elsewhere.

Today, I downloaded a .torrent file to my desktop and, on opening it with Azureus, got the following error message:

[list][i]Not a File0PILOTNot a File0-Not a File0CASANot a File0NONot a File0VOXNot a File0--Not a File0JamendoNot a File0-Not a File0OGGNot a File0VorbisNot a File0q8Not a File0-Not a File02005.07.15Not a File0%5Bwww.jamendo.com%5D.torrent' could not be opened:

Not a File[/i][/list]

Another popup box suggested, *Ensure sufficient temporary file space available (check browser cache usage)*.

I'm buggered if I know what this can be.  There's over 12 GB free in my /home partition, and the fact that there are other problems leads me to suspect it's just the package that's broken.

Any ideas?[/QUOTE]
I get the same problem if I save the torrent file to my hard-disk and then open it from there. If I let firefox/swiftfox open the file with Azureus then it works fine.

** DeadEyes** this is a known problem, but can be worked around. What did the popup box say?

---

### Post by DeadEyes on 2006-06-08
I can't remember exactly but I was using the wizard but was getting NAT errors so I cancelled out to change my router settings when I open Azureus again the message box popped up. the gist of the message was that I should check Azureus' logs

---

### Post by stoeptegel on 2006-06-08
[QUOTE=WebDrake]
And ... does someone know how to check, in KTorrent, that NAT/firewall/router issues are sorted?  Azureus was claiming a DHT error earlier but I'm not sure I trust that package.[/QUOTE]

Look in the log (file or plugin) for this message:
Authentication**(S)** to xx.xxx.xxx.xx : ok

When you can't find an authentication line with an (S) somewhere, you're firewalled on all ports.

---

