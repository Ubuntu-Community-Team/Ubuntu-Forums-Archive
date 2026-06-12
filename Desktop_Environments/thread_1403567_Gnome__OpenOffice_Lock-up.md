---
title: "Gnome / OpenOffice Lock-up"
date: 2010-02-10
forum: Desktop Environments
---

### Post by cilynx on 2010-02-10
Thoroughly repeatably, OpenOffice locks up on me when scrolling inside documents.  Here's the breakdown:

* Only happens when actively in the process of scrolling
* Doesn't matter if you use keyboard, mouse wheel, drag the scroll bar, or click the scroll arrows
* Always happens within 15 minutes of steady use
* Happens in both writer and calc -- haven't tested the others
* OOo freezes up and no longer repaints the window or responds to anything
* gnome-session peaks out at 100% CPU and stays there
* Currently running application continue to work fine
* Most applications (gnome-terminal, firefox, koffice) can no longer be launched
* Some applications (abiword) can still be launched
* Launching from icons brings up the spinner, but nothing else happens
* Launching a GUI app from a terminal, it looks like it runs on CLI, but nothing ever happens in the GUI proper
* X starts leaking descriptors and thus chewing up drive space at ~1M/s

Killing X and bringing up a new session puts everything back to normal, including CPU usage and drive space.  This happens every time on my 64-bit Intel laptop and has persisted through several X/OpenOffice/kernel updates.  It never happens on my 32-bit Intel desktop.

I googled around quite a bit, but never came upon anything like a solution.  Anyone have any ideas?

TIA

---

### Post by bonusiso on 2010-06-17
It was long time ago but i have the same issue. I haven't tried except word. 

But i have also recognised that it happens while i'm scrolling around an image that i have added to the document.

It happens on my 32-bit Intel Core(TM)2 Duo CPU T5450 Notebook.
OpenOffice.org version: 3.1.1

Is there any submitted bug about this.

---

### Post by Hagar Delest on 2010-06-17
Try the latest version from Sun/Oracle: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Make sure that the pic has been embedded inside the file: in the menu Edit>Links (if active), select all the links and disconnect them.

NB: under W2k, I've experienced such freeze when scrolling too quickly, especially if done before OOo has ended the document pagination (when the file is loaded).

---

### Post by bonusiso on 2010-06-21
I have been taking an error while logging in yo gnome about the /home/userXY/.ICEAuthority which could not be updated. I checked the file and its owner was root and it was a binary file. 

I simply removed it and starting from that moment my OpenOffice.org works without any crash. 

Kind Regards,

---

