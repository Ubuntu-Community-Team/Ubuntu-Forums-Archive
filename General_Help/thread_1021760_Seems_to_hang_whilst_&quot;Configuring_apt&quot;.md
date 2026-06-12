---
title: "Seems to hang whilst &quot;Configuring apt&quot;"
date: 2008-12-25
forum: General Help
---

### Post by aussiedaddy on 2008-12-25
I am trying to install Ubuntu 8.10 on a Medion Akoya E1210 netbook (purchased from Aldi) using wubi.

I copied wubi.exe and the Ubuntu 8.10 iso image via a USB drive to the netbook and all seemed to go well until I rebooted into Ubuntu.  The "Checking the installation" process started up and continued, with no apparent error, until it came to the stage where it displayed 82% completion, "Configuring apt" in bold above that and "Scanning the mirror..." in italics below. It apparently "froze" at this point although the inbuilt mouse pad still works.

Can anyone offer any suggestions? :confused:

Thanks

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by aussiedaddy on 2008-12-25
I did some more searching on the net.  It seems that it hangs trying to download information from the Ubuntu repositories.  I followed the advice and removed my network cable and the installation finished and I could boot up into Ubuntu.

There currently seems to be some problem with the Ubuntu repositories so I'm having trouble downloading package information but at least I have Ubuntu running.

---

### Post by aussiedaddy on 2008-12-26
The problem is with file download to the netbook over its ethernet connection.  I can download the package lists to my desktop via the same internet connection in next to no time.  Does anyone know how to copy package lists from one computer to another?

---

### Post by blacksocks on 2009-01-16
I just let it sit there for maybe 20 to 30 minutes and it finally got past 82% and completed the installation.

---

### Post by aussiedaddy on 2009-01-18
Hi blacksocks

Thanks for your response.

I had further issues with UTP ethernet having gotten Ubuntu installed.  Couldn't get the system updates to install.  Just vacationed with a relative and used his network / internet connection and everything worked perfectly so it seems to be some sort of incompatibility between the E1210 and my local network - possibly the Netgear firewall / router / switch.

Thanks again

---

