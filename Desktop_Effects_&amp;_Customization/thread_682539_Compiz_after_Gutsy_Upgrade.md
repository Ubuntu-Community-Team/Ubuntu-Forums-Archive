---
title: "Compiz after Gutsy Upgrade"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by Nessa on 2008-01-30
I can access CCSM but no effects. I've searched through similar threads and installed xgl but that seemed to only make it worse. Any ideas?

---

### Post by ayoli on 2008-01-30
If you had installed compiz from Trevino repository before upgrading to gutsy, you need to completly remove Trevino repository from your apt sources, uninstall compiz and compiz related packages, remove old compiz settings (in ~/.config/compiz and in gconf). 
This [thread]("http://ubuntuforums.org/showthread.php?t=533201") can help to completly remove an old compiz install.
Then reinstalling desktopeefects and compiz package from the ubuntu repository.

---

### Post by Nessa on 2008-01-30
I did that. Reinstalled CCSM. I open it up. It's empty. No preferences, etc... :(

---

### Post by Nessa on 2008-01-31
I reinstalled xgl and it turns out there were some compiz packages that somehow didn't get reinstalled. Reinstalled those components, ran compiz, compiz --replace, metacity --replace in terminal in no particular order with restarts in between. It is working fine again. 

When I run glxinfo | grep -i direct, I get: direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose). I was under the impression that it had to say yes for CCSM to work. Not sure how this setup worked for me. 

Anyway, thanks to all of you. I wouldn't have been able to fix this without the abundance of information in this forum. I hope you figure out the solution to your issues. I'm off to my next project. Mac4Lin on another user account. Ciao!

---

