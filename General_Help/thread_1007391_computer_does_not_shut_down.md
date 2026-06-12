---
title: "computer does not shut down"
date: 2008-12-10
forum: General Help
---

### Post by CommieTechie on 2008-12-10
I am running ubuntu 8.04, and I've never had this problem before until recently. When I go to shutdown the computer, it closes all open programs and such, and then displays the wallpaper I have set. Normally it would display the wallpaper for a few seconds and then start the shutdown process, but now it just... hangs. It will display the wallpaper indefinatly. 

My USB mouse still works when it is on this screen. This process will hang without end forcing me to do a hard restart. On a related note, my External HD and my built in camera no longer mount on startup, I am guessing due to the hard shutdown that I am forced to do.

---

### Post by Dr Small on 2008-12-10
What happens if you try to shutdown the system from the terminal?
Try:
```
sudo shutdown -h now
```

---

### Post by CommieTechie on 2008-12-10
If I shut down from the terminal using that process, it beeps loudly, displays some message (it flashed by to quick to read). It closes everything, and goes to a black screen displaying several Network Manager error messages, then goes to the bootsplash and finishes shutdown normally.

When I restarted it had mounted the external and the built in camera, I am assuming because it had a proper shutdown instead of a hard one like before. At least now I can use this method, but I'd prefer to use the normal way. Any idea what might be causing this?

---

### Post by CommieTechie on 2008-12-10
bump for help

---

### Post by CommieTechie on 2008-12-10
anybody?

---

