---
title: "Problem with Xgl"
date: 2006-06-24
forum: Desktop Environments
---

### Post by haani on 2006-06-24
hi sometimes when i close a program the boarders of the program remain on the desktop. like shown in the pic below how can i overcome this problem?? This only happens with some of the programs.

[IMG]http://img224.imageshack.us/img224/134/screenshot8sa.png[/IMG]

---

### Post by haani on 2006-06-24
23 views and still no reply??

---

### Post by evil_elman on 2006-06-24
I've also got XGL + Compiz installed and immediately found two problems, one of them could be connected or similar to yours:

1. The ALT+TAB feature didn't work properly. This was resoled by starting the Gnome configuration editor (Look in Alacarte menu editor), open 'apps' then 'compiz' and then edited the config in the 'Switcher' folder.

2. Windows weren't minimized or stayed open on the Desktop. I figured this out when I noticed that when I right click-clicked on a window title bar where there was an option to 'unminimize' which shouldn't be possible if the window isn't minimized. The problem was the Dock at the bottom of the screen which frequently crashed for me all the time. I disabled it and is using the regular panels instead now. You can disable it in the Configuration editor.

It might not be the solution but may bring you closer to one, perhaps...

---

### Post by haani on 2006-06-25
[QUOTE=evil_elman]I've also got XGL + Compiz installed and immediately found two problems, one of them could be connected or similar to yours:

1. The ALT+TAB feature didn't work properly. This was resoled by starting the Gnome configuration editor (Look in Alacarte menu editor), open 'apps' then 'compiz' and then edited the config in the 'Switcher' folder.

2. Windows weren't minimized or stayed open on the Desktop. I figured this out when I noticed that when I right click-clicked on a window title bar where there was an option to 'unminimize' which shouldn't be possible if the window isn't minimized. The problem was the Dock at the bottom of the screen which frequently crashed for me all the time. I disabled it and is using the regular panels instead now. You can disable it in the Configuration editor.

It might not be the solution but may bring you closer to one, perhaps...[/QUOTE]


can u explain it in more detail on how did u configure it. i think that really doesnt solve my problem. i havent got dock enabled anywayz

---

### Post by evil_elman on 2006-06-25
If my memory serves me right I solved problem #1 by doing the following:

1. Open up the Gnome Configuration Editor (can be found with Alacarte).
2. Open up the 'Apps' folder.
3. Open the 'compiz' folder.
4. Open the 'plugins' folder.
5. Open the 'switcher' folder.
6. Open the 'Screen0' folder.
7. Open the 'options' folder.
8. Uncheck the 'mipmap' option. 

The 'mipmap' option was checked by default for me and when I unchecked it the Switcher worked fine. When trying to enable it again I can't see any adverse effects but it was a problem then, anyway.

I resolved problem #2 by simply de-activating the 'Dock' at the bottom of the screen. I've seen many others who've experienced buggy behaviour with that thing. You de-activate it by doing the following:

1. Follow steps 1-3 above.
2. Open the 'general' folder.
3. Open the 'allscreens' folder.
4. Open the 'options' folder.
5. The 'active plugins' key lists what modules are started when you log in. Open it up and remove the 'dock' item.

The Dock is now not loaded at all...

I don't know more than this, I'm afraid. The XGL/Compiz system is working fine for me know...

By the way... How is that laptop of yours working? I've been thinking of upgrading my current laptop to something a bit better and I've seen it in the UK at competitive prices...

---

### Post by haani on 2006-06-25
[QUOTE=evil_elman]If my memory serves me right I solved problem #1 by doing the following:

1. Open up the Gnome Configuration Editor (can be found with Alacarte).
2. Open up the 'Apps' folder.
3. Open the 'compiz' folder.
4. Open the 'plugins' folder.
5. Open the 'switcher' folder.
6. Open the 'Screen0' folder.
7. Open the 'options' folder.
8. Uncheck the 'mipmap' option. 

The 'mipmap' option was checked by default for me and when I unchecked it the Switcher worked fine. When trying to enable it again I can't see any adverse effects but it was a problem then, anyway.

I resolved problem #2 by simply de-activating the 'Dock' at the bottom of the screen. I've seen many others who've experienced buggy behaviour with that thing. You de-activate it by doing the following:

1. Follow steps 1-3 above.
2. Open the 'general' folder.
3. Open the 'allscreens' folder.
4. Open the 'options' folder.
5. The 'active plugins' key lists what modules are started when you log in. Open it up and remove the 'dock' item.

The Dock is now not loaded at all...

I don't know more than this, I'm afraid. The XGL/Compiz system is working fine for me know...

By the way... How is that laptop of yours working? I've been thinking of upgrading my current laptop to something a bit better and I've seen it in the UK at competitive prices...[/QUOTE]


thanks but now i fixed by configurin the mininize and scale option. i also live in the uk m8 in tunbridge wells. i bought my laptop for about £845 and its workin gr8!!

---

