---
title: "mame - frontends? problems"
date: 2006-09-03
forum: Gaming &amp; Leisure
---

### Post by bplus on 2006-09-03
Hi,
When I search of a front end for mame using synaptic all I can't find anything except for kxmame

When I use that it won't find my roms even if I point it to the right directory (by specifying the rom path in the menu) and rebuild the game list.

I ve tried gxmame by downloading the deb package and installing it but Im having the same probelms with it - no games being found.

Anybody got any ideas?

P.S Im using ubuntu dapper drake and i got xmame common and xmame-sdl installed and they work fine from the command line.

thanks in advance.

---

### Post by DoktorSeven on 2006-09-03
1) Make sure the Xmame executables option in g/kxmame are pointing to your xmame executables (xmame.x11/xmame.SDL/etc).
2) Make sure when you browse for the executable or ROM path that you then **+Add** that to the list under it (that's tripped me up several times).
3) "Rebuild Game List" is for when you first run g/kxmame (after adding your xmame executables) or upgrade xmame itself to generate a list of possible games to run.  To make it look for your ROMs, hit **Refresh**.

---

### Post by bplus on 2006-09-04
thanks for that got it working eventually!

---

