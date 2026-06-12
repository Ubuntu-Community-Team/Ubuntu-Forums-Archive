---
title: "Beryl/XGL Problem"
date: 2007-03-04
forum: Desktop Environments
---

### Post by robcolclough on 2007-03-04
Hi there,

I'm relatively new Ubuntu so please consider me a newbie and forgive me for inevitably explaining everything in a Windows way!

I've recently installed Edgy and once I got the hang of it I went on to installing Beryl as I could not resist the eye candy it offers and I am really happy with it... It looks fantastic.

I encountered a few issues most of which I've sorted on my own (restart/shutdown buttons disappearing etc) but there is one that remains: As soon as I installed Beryl I lost the background image that is displayed behind the Ubuntu splash screen. The background to my login screen is fine and present and also my desktop background is fine, it's just in between those two stages I get a fussy picture composed of repeating greyscale horizontal bars (if that makes any sense).

I have a hunch that it may not be beryl but could be the drivers I installed at the same time, which I think this is XGL (I am running an ATI mobility X700 in my laptop).

I followed this guide to install XGL and Beryl. [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

Forgive me for jumping straight into the forums on this one but it's a tricky one to search for "repeating horizontal greyscale gradient problem in beryl" doesn't come back with too many results! Any suggestions would be greatly appreciated. 

Thanks in Advance

Rob

---

### Post by ffxr on 2007-03-04
try adding this to the device section of xorg.conf, back it up and know how to restore iin case it breaks..

```
 Option      "MonitorLayout" "LVDS,NONE" 
```

ull need to restart x to see if it works..

do a search for 'x700 beryl' if it doesnt help..

---

### Post by robcolclough on 2007-03-04
No cigar.....

I tried what you suggested and it made no difference. Searches comes up with nothing.

I also tried adding and changing the login window theme, my desktop background and the ubuntu splash image in order to try and apply some kind of graphic to the splash background -none were successful.

Any ideas?

If it helps when the splash screen shows my cursor changes to a black X with a white border.

Thanks again

Rob

---

