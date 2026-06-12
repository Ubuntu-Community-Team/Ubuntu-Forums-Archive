---
title: "a fix for cups paused printer"
date: 2006-07-09
forum: Desktop Environments
---

### Post by mvaranda on 2006-07-09
I had a printing in progress requested by a client machine. Because the printing was not what I wanted then I have decided to stop it in the server machine. So I stoped the printer (HW) and used the "pause" command available in the printer GUI.

After that I could not  recover that printer anymore. That was a raw drivers in the server so any client machine could not print anymore. However, the server machine could print OK using the local print driver (both raw and local were using the same physical printer).

The only way I got that back working fine was using the  CUPS web interface.
However, I needed to enable the administration access for it:

I followed the tips in the link "http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/" which says:
"If you are trying to get your printing system going, and search for tips and docs on the web, you will find most of the documentation referring to [http://localhost:631](http://localhost:631) as your cupsys administration interface. However, on Ubuntu, this browser-based administrative interface for cupsys is disabled by default. Here’s how to enable it:

Select “System”->”Administration”->”Users and Groups” from the main menu on your desktop.
Select “Show all users” and/or “Show all groups”.
Add the user “cupsys” to the group “shadow” in the “groups” tab.

Restart cupsys by issuing the command:
$sudo /etc/init.d/cupsys restart"

Having that setup then just use your browser to go to "http://localhost:631".

Go to the "printers" and press the button "Start".

Yup... it looks so easy but took me a quite while. This text was meant to save you some time :-)

Cheers

---

