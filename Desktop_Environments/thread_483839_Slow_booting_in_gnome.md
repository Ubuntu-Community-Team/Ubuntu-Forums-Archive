---
title: "Slow booting in gnome"
date: 2007-06-25
forum: Desktop Environments
---

### Post by granjerox on 2007-06-25
Something happens in my ubuntu 7.04 since 3 days. When gnome boots its stuck at the bootsplash when it says Nautilus. One minute or so later it finish booting. I don't know whats the program or service that is interrumping the boot process. Any idea?

---

### Post by rax_m on 2007-06-25
I am assuming you mean the time from when you log in to when you have a usable desktop right?

If you go to System->Preferences->Sessions  then look at the Startup Programs tab  you can see what programs are configured to start when you log in. You may have added something in there..  if you're not sure, probably don't disable it. 

Also what spec machine do you have?

---

### Post by stueyboy on 2007-06-25
I'd be interested to see what is causing this as I now have exactly the same problem after installing compiz fusion. I have tried to disable it from the startup and I still get the slow splash so I wonder if it's something else installed at the time.

EDIT: In case it's important, I noticed a regular network spike in the system manager about once a second while the nautilus splash screen was hanging on the desktop

---

### Post by santarulz on 2007-07-05
Edit: I believe the solution can be found here:

[http://ubuntuforums.org/showthread.php?t=487102](http://ubuntuforums.org/showthread.php?t=487102)

---

### Post by stueyboy on 2007-07-05
Thanks for that. I needed to completely remove beryl which I hadn't done and the startup script with the delay works a treat now.

---

