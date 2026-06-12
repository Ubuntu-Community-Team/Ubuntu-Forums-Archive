---
title: "Evolution error: couldn't read 4 bytes from client"
date: 2009-03-11
forum: General Help
---

### Post by wigren on 2009-03-11
I just started using Evolution as my email client. Every thing works fine, except when I check /var/log/auth.log I see this error over and over:

Mar 11 06:36:05 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client: 
Mar 11 06:36:05 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client: 
Mar 11 06:39:05 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client: 
Mar 11 06:39:05 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client: 
Mar 11 06:42:05 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client: 
Mar 11 06:42:05 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client: 
Mar 11 06:45:06 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client: 
Mar 11 06:45:06 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client: 
Mar 11 06:48:31 acer gnome-keyring-daemon[6005]: couldn't read 4 bytes from client:

Like I said, every thing is working. But I wish this error was not eating up so much log space every three minutes. Any other references to the error that I can find online all mention KDE not working well with gnome-keyring-daemon, but I use GNOME. Any help is appreciated.

---

### Post by Jgonick on 2009-03-27
You are not alone... I'm getting the same error, and like you everything seems to be working other than the error in the log.  Any help would be appreciated even though this is not a major problem just annoying.

---

### Post by wigren on 2009-03-30
I upgraded to Intrepid over the weekend to see if the problem persists. It did not! I have issues with Intrepid though, so I'll live with the error for a while longer I guess. But I am glad to hear I'm not alone.

---

### Post by dcstar on 2009-03-31
> **Jgonick said:**
> You are not alone... I'm getting the same error, and like you everything seems to be working other than the error in the log.  Any help would be appreciated even though this is not a major problem just annoying.

It's not even a "minor" problem as it does not affect anything working on your system at all. It puts entries in the log file - big deal.

---

