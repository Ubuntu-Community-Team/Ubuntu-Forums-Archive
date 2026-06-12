---
title: "can't change keyboard in Ubuntu"
date: 2007-05-09
forum: Desktop Environments
---

### Post by moose6589 on 2007-05-09
Hi, 

Starting this morning, I realized that the Alt keys on my laptop (Dell E1405) no longer function properly. I am no longer able to browse back and forward in Nautilus or Firefox with Alt+Left and Alt+Right, which is rather annoying. 

However, the Alt key isn't broken since all my Beryl shortcuts with Alt still work, such as changing opacity and Ctrl+Alt+Left/Right. Somehow, Alt is working but has lost some of its functionality. 

I tried to change keyboard settings under System-->Preferences but it threw me an error, and I have also been getting the same error when I restart X or boot up. The error message is attached. Furthermore, I am also getting that message about whether I want to use Gnome or X's settings for my keyboard because the settings somehow differ. 

Does anyone know what is going on here? The Alt key is still working perfectly fine on my desktop system. Thanks. 

P.S. Here is the output from the two commands in the error message. 

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "us-dvorak", "dvorak", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us", "dvorak", "grp:alts_toggle"

and 

 layouts = [us  dvorak]
 model = 
 options = [grp grp:alts_toggle]
 overrideSettings = true

---

