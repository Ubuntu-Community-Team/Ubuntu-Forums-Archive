---
title: "Can't see windows, icons, anything"
date: 2011-01-23
forum: Desktop Environments
---

### Post by Gex010 on 2011-01-23
hi guys, I was stuffing around with one of the opacity settings in compiz and I think I set everything to 100% opacity (don't ask, I have no idea)

So basically all I can see is my background, I know that the windows and menu are there because the burn effect still shows if I click where my applications menu should be.

I think if I can kill compiz everything will switch back to metacity but how can I do this from command line.

when ubuntu, I press alt+ctrl+f1 to get tty1 then i can at least do something but dunno what command switch to another theme manager.

I tried "sudo metacity --replace" but that did not seem to work.

pleeeaasssseee I need urgent help!

---

### Post by Gex010 on 2011-01-23
Sorry guys, was being abit stupid there just had to do an alt+f2 killall compiz

strange thing is that I could not do a killall compiz from tty1???

---

### Post by Krytarik on 2011-01-23
LOL, I also had to do it twice recently, also pressing Alt+F2, but entering "metacity --replace" instead.
> **Gex010 said:**
> Sorry guys, was being abit stupid there just had to do an alt+f2 killall compiz
strange thing is that I could not do a killall compiz from tty1???
I guess because "it" doesn't know on which display it shall do this. With the correct "DISPLAY" parameter it would probably work.

---

