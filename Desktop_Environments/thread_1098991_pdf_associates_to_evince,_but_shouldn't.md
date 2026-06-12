---
title: "pdf associates to evince, but shouldn't"
date: 2009-03-17
forum: Desktop Environments
---

### Post by pteehan on 2009-03-17
I use acroread for .pdf's.  I've set the file associations and it works fine.  When I double-click on a pdf it opens in acroread.  

I use firefox with zotero.  I have firefox configured to open pdf's in acroread (externally, not a plugin).  But there is one particular action in zotero, the "View Snapshot" feature, that always launches pdf's in evince.  I can find no trace of evince in my firefox or zotero preferences.  

The behavior is the same as that described in the 13th message in [this thread]("http://forums.zotero.org/discussion/2241/?Focus=11459") on the Zotero forums (CB, Jun 9th 2008 ).  The issue there was never solved; there was speculation that it is an OS problem.

I've looked for information on this but don't know enough to understand what I've found.  I understand there are global associations in /usr/share/applications and local associations in ~/.local/share/applications.  

In the global associations in /usr/share/applications/defaults.list there is this line:
application/pdf=evince.desktop

In the local associations in ~/.local/share/applications/mimeapps.list there is this line:
application/pdf=userapp-acroread-MJLNKU.desktop;evince.desktop;AdobeReader.
desktop;gimp.desktop;

My understanding is that the local settings are supposed to override the global settings.  I thought maybe the first .desktop is not being found so I changed it to this:
application/pdf=userapp-acroread-MJLNKU.desktop;AdobeReader.desktop;evince.desktop;gimp.desktop;

But doing so had no evident effect, even after restarting Ubuntu.

I would be happy to keep tinkering but don't know what I'm doing and don't want to break anything and could use some guidance.  Thanks.

---

