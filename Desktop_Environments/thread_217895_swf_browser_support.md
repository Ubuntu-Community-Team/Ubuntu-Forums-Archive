---
title: "swf browser support"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Isoss on 2006-07-17
I am using firefox and konqueror for web browsing. I have all the plugins installed and everything is fine. Except that swf, althought working, but too slow! I have a folder of flash games and they used to play perfectly in IE back in windows. I can play these games now but they are slow .. and I mean like they slowdown every minute or like once between shots in a gun game.
Why is that? I have a good machine and this happenes on my PC and my laptop as well!

Hope someone has a solution!

---

### Post by x64Jimbo on 2006-07-17
It's because Adobe/Macromedia refuses to open the source code for their flash plugins. They write it all in house but don't think it's worth spending the time to make it work well in Linux. 
If you want your Flash stuff to work pretty flawlessly, you should look into running the Windows version of Firefox through wine, then installing the flash plugin there. I've been doing that for a while and it seems to work pretty well. 
If you want to do something about it, write to Adobe/Macromedia and tell them to pull their collective heads out of their poopers.

---

### Post by Isoss on 2006-07-18
Thanks. but what firefox version is guaranteed to work well?

---

### Post by mattisking on 2006-07-18
> **Isoss said:**
> Thanks. but what firefox version is guaranteed to work well?
Just for clarification, any current version of Firefox for Windows should work fine. The problem here isn't Firefox, it's Macromedia's (well Adobe's now) Flash Player. Flash Player is only supported up to version 7 on Linux and not all that well at that. Flash 9 is supposed to support Linux early next year. In the mean time, if you find yourself needing better flash support, you'll need to run under Wine (which I've never tried myself). Since you can't run the plugin itself under Wine, the only way to run a current version of the Flash plugin is to run both the Firefox browser and the plugin under Wine. So, download and install the latest 1.5.0.4 version of Firefox from the main website ([www.mozilla.com](www.mozilla.com) will work) and install using wine. Then, while running that browser under wine, go to [www.macromedia.com/shockwave/welcome/](www.macromedia.com/shockwave/welcome/) and it should let you install Flash from there very easily.

---

