---
title: "Switching default file manager to Dolphin-kde4"
date: 2008-12-24
forum: Desktop Environments
---

### Post by mnemonik on 2008-12-24
Hello all!

I followed this tutorial ( [http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html](http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html) ) while trying to switch my default file manager to dolphin (because I want the column view that is similar to Finder's in OSX) and now dolphin-kde4 is my default filemanager when opening folders from the "places" menu, but not when I open a folder that is sitting on the desktop. When I do that it just opens in nautilus. Is there a config file that would let me fix this problem?

I have seen another tutorial on switching file managers that seems more complete here: ( [http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease) ) but it doesn't have any help with dolphin.

Thanks guys.

---

### Post by ldrn on 2009-01-18
You've probably already found a solution, but I wanted to do the same thing, so I modified the konqueror script from that page to use dolphin instead -- for future thread searchers, I attached it. :) All I did was add a line using sed to replace konqueror with dolphin before the scripts are chown'ed:

sed -i 's/konqueror/dolphin/g' *.desktop

It seems to be working well for me.

---

