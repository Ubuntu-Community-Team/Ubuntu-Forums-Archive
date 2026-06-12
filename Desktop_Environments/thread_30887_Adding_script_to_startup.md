---
title: "Adding script to startup"
date: 2005-04-30
forum: Desktop Environments
---

### Post by mortram on 2005-04-30
I have my slmodem drivers installed and working in Kubuntu.  I can start the modem manually by typing:

sudo /usr/sbin/slmodemd /dev/slusb0

and leaving that process running.

The slmodem .tar comes with a debian startup script called 'slmodemd' that I copied to /etc/init.d/.  Now how do I get that script called at startup so the modem device is initialized at boot?

I was able to do it with Fedora, but only through some guessing and the 'server settings' GUI.

Googling has only given me undecipherable info regarding the matter.  Seems like there's probably a simple way to do it.


Thanks!

---

### Post by Takis on 2005-04-30
Make a link to it from /etc/rcS.d/SxxYYYYYYYYY

Where xx is a two-digit number specifying when in sequence to run the script, and YYYYYYYYYYY is a name to identify your script (usually you call it the same name as the script in your init.d directory).

---

