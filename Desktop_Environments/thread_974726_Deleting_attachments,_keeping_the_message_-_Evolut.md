---
title: "Deleting attachments, keeping the message - Evolution"
date: 2008-11-07
forum: Desktop Environments
---

### Post by handaxe on 2008-11-07
Ever wanted to reduce mailbox storage but was prevented from doing so by the need to keep the messages having those huge attachments?

Thanks to Rex Tsai you now can via his plugin for evolution. It is available as a .deb on his PPA: [https://launchpad.net/~chihchun/+archive]("https://launchpad.net/%7Echihchun/+archive")

Written for Ubuntu 8.4 and evolution 2.22 for which installation presumeably is straightforward, you can easily deploy this for 8.10 and 2.24 by extracting:
org-gnome-remove-attachments.eplug
org-gnome-remove-attachments.xml
liborg-gnome-evolution-remove-attachments.so 

from the .deb and copying them to '/usr/lib/evolution/2.24/plugins'. 

A quick edit within 'org-gnome-remove-attachments.eplug' (use gedit or some such) to change the plugin path from 2.22 to 2.24 and you are good to go.

To use, highlight the attachment bearing mail and right mouse click to bring up a menu with a 'remove attachments' option. Be warned, when selected it simply does the job without further enquiry.  The attachment is replaced by the name of the file and a message that it was removed.

Very very useful if you need to archive your mail for whatever reason. 

HA

Ref: [http://ubuntuforums.org/showthread.php?t=655386](http://ubuntuforums.org/showthread.php?t=655386)

---

### Post by cmcqueen1975 on 2009-05-05
Is it safe to do this for Ubuntu 9.04 (Jaunty) with Evolution 2.26?

---

### Post by handaxe on 2009-05-05
I have this working under Ubuntu 9.04 and Evolution 2.26.

HA

---

### Post by bigchrisrogers on 2010-01-15
Thanks for the help here, I have this working in 9.10 and 2.28, dead easy.

---

### Post by bobzr on 2010-04-23
> **bigchrisrogers said:**
> Thanks for the help here, I have this working in 9.10 and 2.28, dead easy.

Unfortunately it doesn't seem to work any longer. I'm also using karmic and evo 2.28 and when I try to add the ppa I get this msg:

Failed to fetch [http://ppa.launchpad.net/chihchun/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/chihchun/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

Does anybody know how to get this useful feature on Evolution, deleting attachments and keeping the message?

---

### Post by handaxe on 2010-04-23
Download the deb directly from [https://launchpad.net/~chihchun/+archive/ppa/+packages]("https://launchpad.net/~chihchun/+archive/ppa/+packages").  Files are still there. Follow directions in first post and it should work.

HA

---

### Post by chitarrino on 2011-05-05
In Natty and Evolution 2.23 it's broken. I managed to get it listed among Evolution's plugins, but the checkbox to enable it is not responding. I guess Evolution detects the incompatibility.
Any hacks/fixes?

---

### Post by mikelito on 2011-05-06
running from a terminal

can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-evolution-remove-attachments.so': /usr/lib/evolution/2.32/plugins/liborg-gnome-evolution-remove-attachments.so: undefined symbol: camel_medium_get_content_object

so it seems the plugin is broken with 2.32
hope a fix comes soon, or that they finally decide to implement natively the possibility of removing attachments.

---

### Post by handaxe on 2011-05-07
I had lost track of this completely :)  I see that Mr Tsai uploaded a new version in Nov 2010 and so he may well sort this out.  I assume you are trying to use the build for Maverick that he provided?

Has anyone submitted a wishlist "bug" to the evolution team for this?

---

### Post by chitarrino on 2011-05-16
No, can you please do that?
Thanks!

---

### Post by chitarrino on 2011-05-27
My temporary workaround was to install Thunderbird and two extensions: Attachment Extractor and Import/Export Tools.
You can then export the mbox from Evolution, import it into Thunderbird and purge it from attachments.

---

