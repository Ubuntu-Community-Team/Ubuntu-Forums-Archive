---
title: "Beryl Stopped Working due to skydomes/no apparent reason!? (details inside)"
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by JuicedJuice on 2007-05-25
Ok, so I was messing around with various skydome images and on the 5th or 6th one I tried, beryl stopped working and pressing ctrnl + alt + mouse to use the cube does nothing. It happened after I had browsed to the skydome image and clicked open, after that moment I couldn't do anything with beryl. I disable the skydomes, made sure the browse path was empty etc and nothing works. I tried uninstalling/reinstalling beryl too but I still can't do anything and after reinstalling there are always the same settings as before (I just can't get them back to the way they were the first time I installed beryl). Is there some way to restore default settings or something or is there a bigger problem? Could it have something to do with desktop effects? Any help is appreciated, thanks.

---

### Post by moljac024 on 2007-05-25
Make sure that beryl is selected as the window manager (right click on the red diamond in system tray). By default Beryl will revert to metacity (the default gnome window manager) if it crashes. 

The reason re-installing didn't help is most likely because uninstalling beryl (or beryl settings manager) didn't delete the configuration files. If you're using synaptic then you should check "mark for complete removal" to get rid of the configuration files of an application...

---

### Post by JuicedJuice on 2007-05-25
Ah yea, it was the windows manager. Every time I booted up it was switching to metacity. Thanks

---

