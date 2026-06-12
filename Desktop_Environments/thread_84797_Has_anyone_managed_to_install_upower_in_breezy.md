---
title: "Has anyone managed to install upower in breezy?"
date: 2005-10-31
forum: Desktop Environments
---

### Post by idn on 2005-10-31
I was wondering if anyone has managed to do this. I got it working in hoary, just wondered if it was still possible to get it working because of usplash.

---

### Post by kanem on 2005-11-02
[QUOTE=idn]I was wondering if anyone has managed to do this. I got it working in hoary, just wondered if it was still possible to get it working because of usplash.[/QUOTE]
Works for me. I had already uninstalled usplash though. Wasn't anything to do to get it working besides add the maintainer's repository (deb [http://repo.nanofreesoft.org](http://repo.nanofreesoft.org) breezy main) and installing.

---

### Post by idn on 2005-11-02
How did you uninstall usplash?

---

### Post by kanem on 2005-11-02
[QUOTE=idn]How did you uninstall usplash?[/QUOTE]
It's visible in synaptic like everything else. But now that I think of it, I may have never installed it in the first place because I already had splashy installed when I upgraded to breezy. I know I've seen usplash, but it may have been on a test installation.

Whatever I did, I don't have it installed now. If I try to install Ubuntu-desktop, it wants to remove upower and install usplash.

---

### Post by idn on 2005-11-06
Ok, I followed the howto [ here]("http://nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1#Download_upower") and everything worked out ok :)

I had to remove my kernel which is always a bit of a risky business, hen remove some restricted modules to get the nvidia drivers to work. Only problem is that I had to remove the ubunu-desktop meta package, so dist-upgrade might be a bit interesting :)

BTW UPower is amazing!

---

