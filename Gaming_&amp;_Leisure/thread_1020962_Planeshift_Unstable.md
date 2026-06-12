---
title: "Planeshift Unstable"
date: 2008-12-24
forum: Gaming &amp; Leisure
---

### Post by tommygunner on 2008-12-24
I have installed Planeshift on Ubuntu 8.10 and it seems to be unstable. I run it as root in order to get it to work. It ends up locking up while in game play. 

I'm wondering if anyone else is having issues with this game.

---

### Post by dannytatom on 2008-12-24
Same thing happened to me the other day, I posted the fix in another thread:

> 
Anyway, I got it installed last night with no problem (almost). I ran the installer as root and let it do it's thing, it installed to /opt, then asked for me to set permissions. If I didn't, only root and people in the "games" group could use it. When ahead with it, after it installed I created a group named 'games,' and added myself to it then did:

```

sudo chown -R root:games /opt/PlaneShift

```

Everything works fine now. Also, it's a pretty nifty game, I think. It doesn't have a big userbase, but the fact that it's so centered around roleplaying keeps me interested.


If you set yourself as owner, you won't be able to update, so the only option (that I could find) is do as above.

**Edit:**  You'll have to uninstall & reinstall to do this.

---

