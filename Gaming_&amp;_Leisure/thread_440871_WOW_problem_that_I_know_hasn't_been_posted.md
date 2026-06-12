---
title: "WOW problem that I know hasn't been posted"
date: 2007-05-12
forum: Gaming &amp; Leisure
---

### Post by phenox on 2007-05-12
I was able to install WOW and BC just fine. wine was also easy to install and im currently using version 0.9.36

ive read a number of howtos already and am still having trouble. right now the sound isn't working and when i launch the game it runs EXTREMELY slow. i've not even made it past the opening cinematics and the license agreement because of how slow it is. in the howtos they suggest changing the Config.wtf file located in /drive_c/World of Warcraft/WTF. problem is, the file does not exist until you login to your character which I can't do because of how slooooow it is.

any help would be greatly appreciated! 

thanks in advance

---

### Post by Ardrias on 2007-05-12
This page [http://www.wowwiki.com/Config.wtf_defaults](http://www.wowwiki.com/Config.wtf_defaults) could maybe help you to create a default one at least.  

Tried passing the -opengl switch? If you put it in config.wtf it shouldnt be needed tho.

---

### Post by ShadowFlar3 on 2007-05-27
You can just create an empty Config.wtf and add what you like, like SET gxApi "opengl" and resolution and stuff that is told about on the guides. Heres one:

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by Nehvrook on 2007-05-27
If youv'e already installed WoW on Windows you can copy and paste that WTF file over and it'll have all your settings and stuff saved too. Then just change the config file and add the stuff you need to make it run properly in Linux (Like SET gxApi "opengl" mentioned above)

Also did you do the registry tweak for WoW? That really helps improve fps

---

