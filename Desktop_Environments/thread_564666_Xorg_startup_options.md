---
title: "Xorg startup options"
date: 2007-10-01
forum: Desktop Environments
---

### Post by Dennisb1 on 2007-10-01
Hello,

I have at the moment 3 pc's where i boot my ubuntu usb hard disk from.
On all these pc's i have to reconfigure xorg to make it work.
Is it possible to choose on startup on a list what config need to be used from a easy 1. 2. 3. menu?
This will make my life much easyer and faster!

Regards,
Dennis

---

### Post by jamarsa on 2007-10-03
Yes, you can although I haven't tried it. From Xorg manual:

>        -config file
               Read the server configuration from file.  This option will work
               for any file when the server is run as root (i.e, with real-uid
               0), or for files relative to a directory in the  config  search
               path for all other users.


So, perhaps you can modify /etc/gdm/gdm.conf to give a environment variable to the command portion of the Standard Server configuration. Or perhaps more simple, overwrite /etc/X11/xorg with a case sentence in /etc/init/gdm, for example depending on your lspci output...
In both cases, a bit of script programming knowledge is desired ;) .

---

### Post by Dennisb1 on 2007-10-06
Hmmm thanks for the information
exept i cant program :(
so if anywone have time or got the file already? this would be great!

---

