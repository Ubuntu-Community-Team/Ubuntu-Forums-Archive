---
title: "left + right = middle click"
date: 2011-06-04
forum: Desktop Environments
---

### Post by sadrak on 2011-06-04
i have a fresh install of Xubuntu on my new Samsung nf210, but i cannot make a middle click anymore. With my old Samsung NC10 i simple have to click both keys (left + right) fast and i get a middle click. With the nf210 i get the the clicks in the order i clicked :-/ Its the same for the mousepad and a usb-mouse.

---

### Post by Copper Bezel on 2011-06-05
There's a Synclient setting for that. If you run synclient -l , you should see something along the lines of EmulateMidButtonTime, and you can run synclient EmulateMidButtonTime=200 or something like that to set it. See if that works - if it does, you'll need to create a script to set this on boot.

---

### Post by sadrak on 2011-06-05
i think i have a bigger problem :-/ my mousepad is a logitech wheel mouse (xinput list) and i found a big bugreport about mousepad & samsung netbooks/laptops ...

So i installed mouseemu and get CTRL + click = middle click as workaround. Where can i disable the menu-key (between alt-gr and right ctrl)?

That would be the ideal middle-click-key, but it is allready bind to: menu ;)

---

### Post by Copper Bezel on 2011-06-05
You could disable it using xmodmap, like

xmodmap -e "keysym Menu = VoidSymbol"

which only works per session - you would need to put the command in Startup Applications. How were you planning to turn it into a middle-click, though? If you don't have a plan for it, there are a few methods to do this - you could look [here]("http://ubuntuforums.org/showthread.php?t=1694352") and see which one makes the most sense for your situation. I think the simplest would be to install xdotool, then use either Keyboard Shortcuts or CompizConfig to bind Voidsymbol to xdotool click 2 .

Sorry to hear about the poor recognition of your device!

---

### Post by sadrak on 2011-06-06
i will first try mouseemu ;) works also with win-key, so it should also work with every other key (when i can disable the normal behavior for that key)

thanks!

---

