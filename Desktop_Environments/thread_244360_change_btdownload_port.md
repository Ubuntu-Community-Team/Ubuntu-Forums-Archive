---
title: "change btdownload port"
date: 2006-08-26
forum: Desktop Environments
---

### Post by librano on 2006-08-26
hi all!

i have a short and quick question...

i would like to change the default port which gnome-btdownload uses to listen for incoming connections (default is 6881, or something close to that)... i know i can change it when i run it from command line using the --minport option... but i would like to change the default port so i dont have to specify each time i run btdownload.

thanks for your help!

cheers.

lib.

---

### Post by moore.bryan on 2006-08-26
*i'm not sure you can.  i had a similar issue and found the best way to resolve it was to switch to bittornado (it's in the repos).  bittornado lets you switch up all that stuff, seems to have a small footprint, and is pretty intuitive.  good luck.*

---

