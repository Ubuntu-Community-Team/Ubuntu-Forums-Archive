---
title: "GDM configuration file?"
date: 2006-01-08
forum: Desktop Environments
---

### Post by Maelgwyn on 2006-01-08
I've just run apt-get dist-upgrade to get to Breezy, and when I restarted, I got this message at the GDM login screen:
 
> 
[SIZE=2]The configuration file contains an invalid command line for the login dialog, so running the default command. Please fix your configuration.

[/SIZE]

---

### Post by Ampersand on 2006-01-08
Have you tried a 
```
sudo dpkg-reconfigure gdm
```
This might reset any files that are causing problems. I've not come across this problem before, so can't suggest  anything else.

---

### Post by Maelgwyn on 2006-01-09
Tried that, and then hit ctrl-shift-backspace (or whatever it is) to restart GNome, and it still gives me the error message =(

---

