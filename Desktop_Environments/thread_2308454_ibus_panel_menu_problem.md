---
title: "ibus panel menu problem"
date: 2016-01-03
forum: Desktop Environments
---

### Post by chasashmore on 2016-01-03
I just installed ubuntu 15.10  (AMD64, with standard unity desktop) from the previous version. First I tried an online update, but couldn't reboot after installation. So I downloaded the dvd and reinstalled from that, without reformatting my /home directory (all else reformatted).

Now I have trouble with the ibus menu on the unity panel. I have the following language layouts that I use and that I have in the panel menu: english (us) as default, sanskrit transliteration, hindi, sanskrit, bengali, spanish, french, swedish, pinyin Chinese. But on the menu that opens from the panel icon, there is an old entry for "m17n:t:sa-translit" which is no longer present, nor needed (it's an old Sanskrit transliteration method). And that seems to be messing up my ability to switch between layouts. 

I have tried to correct it through dconf-editor, gconf-editor, and ibus-setup, and none of those shows this entry for the old transliteration method which no longer exists, and so there is nowhere I can find that allows me to delete it. If I open the ibus menu on the panel, and then select "Text Entry Settings", that also doesn't have that obsolete method listed. And yet there it is, still in the menu, and it seems to be what is defeating my ability to switch keyboards easily by a key combination: I have to go to the menu with the mouse to select.

One last thing I tried: I've tried to uninstall everything connected with ibus that doesn't require uninstalling the desktop itself, and I did the purge, so that config files were also deleted, but that didn't help when I reinstalled. And I tried a forced reinstall of everything including the parts of the ibus system that the desktop depends on. Nothing helps. The entry is still there.

Anyone know how to find where the panel menu stores the selections, so that I can delete the entry? Thx.

---

