---
title: "troubleshoot libreoffice locking computer"
date: 2017-08-24
forum: Desktop Environments
---

### Post by dgermann on 2017-08-24
Friends--

How would you troubleshoot this issue?

Issue: LibreOffice locks up the entire computer. Hard reboot is necessary. By lock up I mean that the clock at the top which shows seconds stops advancing. Occasionally it happens with other programs.

Production environment. We have similar problems with 3 other machines, but on those LO seems to crash and have to be re-started.

All machines are Ubuntu 16.04 lts, using gnome, and have both whole disk encryption and home directories encrypted. LO is version 5.1.6.2, from Ubuntu repositories. Pretty plain vanilla. Network is cifs to a 14.04 machine.

Most often it seems that the behavior happens as we click on the "x" in the corner to close a document, or to close out of a file in PDFStudioPro12. Often it seems that Nautilus is involved. The person on this computer will usually have open Nautilus, LO, and PDFStudioPro12 simultaneously. (The other users rarely if ever use PDFStudioPro12).

Here are the last 10 entries from /var/log/syslog from three recent crashes:
```
Aug 24 17:27:04 yarn org.gnome.Nautilus[1888]: (soffice:17991): Gdk-WARNING **: gdk_window
_set_icon_list: icons too large
Aug 24 17:27:11 yarn org.gnome.Nautilus[1888]: W: Unknown node under /registry/extlang: de
precated
Aug 24 17:27:11 yarn org.gnome.Nautilus[1888]: W: Unknown node under /registry/grandfather
ed: comments
Aug 24 17:27:11 yarn org.gnome.Nautilus[1888]: W: Unknown node under /registry/grandfather
ed: comments
Aug 24 17:28:47 yarn systemd[1]: Started CUPS Scheduler.
Aug 24 17:28:47 yarn colord[1156]: (colord:1156): Cd-WARNING **: failed to get session [pi
d 20879]: No such device or address
Aug 24 17:28:47 yarn colord[1156]: message repeated 3 times: [ (colord:1156): Cd-WARNING *
*: failed to get session [pid 20879]: No such device or address]
Aug 24 17:28:58 yarn org.gnome.Nautilus[1888]: (soffice:17991): Gdk-WARNING **: gdk_window
_set_icon_list: icons too large
Aug 24 17:30:12 yarn org.gnome.Nautilus[1888]: (soffice:17991): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
Aug 24 17:30:26 yarn org.gnome.Nautilus[1888]: Warning: failed to read path from javaldx
Aug 24 17:30:27 yarn org.gnome.Nautilus[1888]: (soffice:20966): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

```
```

Aug 21 16:41:13 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 34
Aug 21 16:41:13 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 36
Aug 21 16:41:13 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 36
Aug 21 16:41:13 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 34
Aug 21 16:41:13 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 36
Aug 21 16:41:13 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 36
Aug 21 16:41:13 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 34
Aug 21 16:41:17 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 36
Aug 21 16:41:17 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown ev
ent notification 36
Aug 21 16:41:17 yarn org.gnome.Nautilus[17616]: ** (soffice:21980): WARNING **: Unknown event notification 34
```
```

Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: ** (soffice:13217): WARNING **: Unknown eve
nt notification 36
Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: message repeated 15 times: [ ** (soffice:13
217): WARNING **: Unknown event notification 36]
Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: ** (soffice:13217): WARNING **: Unknown eve
nt notification 37
Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: ** (soffice:13217): WARNING **: Unknown eve
nt notification 36
Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: message repeated 15 times: [ ** (soffice:13
217): WARNING **: Unknown event notification 36]
Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: ** (soffice:13217): WARNING **: Unknown eve
nt notification 37
Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: ** (soffice:13217): WARNING **: Unknown eve
nt notification 36
Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: message repeated 15 times: [ ** (soffice:13
217): WARNING **: Unknown event notification 36]
Aug 17 13:16:28 yarn org.gnome.Nautilus[1876]: ** (soffice:13217): WARNING **: Unknown event notification 37
Aug 17 13:17:01 yarn CRON[13632]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 17 13:17:21 yarn org.gnome.Nautilus[1876]: ** (soffice:13217): WARNING **: Unknown event notification 36
```

Searches on "icons too large" and "unknown event" have not proved fruitful.

We have tried letting the machine sit for 5 or 10 minutes after a lock up, and it does not start up on its own. We have tried leaving Nautilus off. No success either one.

On another machine, I have noticed that when I have multiple LO docs open, print one, then close it using the "x" in the upper right corner, that's when LO crashes.

What would be some steps I can take to narrow down this problem?

Thanks!

---

