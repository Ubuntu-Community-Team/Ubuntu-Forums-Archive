---
title: "How to c hange default keyboard language during boot?"
date: 2009-06-13
forum: General Help
---

### Post by theosap on 2009-06-13
Dear Ubuntu members,

since yesterday I've been facing a problem with my ubuntu laptop and I still haven't managed to resolve it. Long story short...somehow I set as default (and possible only) keyboard language in my system to be the Greek. When I start my system I need to enter my user/pass and since i can't type english i can't login at all.

Currently I can edit my system files thanks to parted magic (live cd), still I dont know what I have to do and havent find any article to say exactly which file I need to edit to fix this. I tried adding:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xkb"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection


to xorg.conf with no difference.

I added "single" in grub line in order to get to option to reset password, not possible since I can't move cursors again (greek letters are passed like [hex ] or something.

Any help will be greatly appreciated, feeling depressed since that happened...

---

### Post by theosap on 2009-06-13
i found solution,i  had to edit:

etc/default/console-setup

and set en as keyboard :)

cheers

---

