---
title: "Nautilus crashes on startup! And some more wierd things happen!"
date: 2009-04-12
forum: General Help
---

### Post by DexterLB on 2009-04-12
For some time, on shutdown I got black screen (I click shutdown or execute "shutdown -P now", and I get black screen until the computer actually powers off).

Yesterday I turned my PC on, and I went to the other room. When I went back, it had frozen on black screen, not catching num lock/caps lock. So I had to horseway-restart it (using the reset button --> I had never done that on Ubuntu before!)

And when I did click shutdown - a miracle! Usplash showed, and it shutted down correctly. Now it always shuts down with Usplash, no black screens :)

But, there's another problem: On startup, nautilus starts, all icons on the desktop appear, and after a few seconds - nautilus crashes! Just the icons disappear, and if I execute "ps -A | grep nautilus", there is no nautilus process. I've done a temporary workaround: made this script ```
#!/bin/bash
sleep 20
nautilus -n&

``` and added it to the sessions configuration, but this is just the "idiot" way to do it. So, has anyone encountered this problem? Should I submit it as a bug in launchpad?

---

