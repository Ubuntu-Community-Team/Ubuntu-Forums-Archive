---
title: "!!! Different Wallpapers for Different Desktops !!!"
date: 2009-04-06
forum: Desktop Environments
---

### Post by Naz_Farooq on 2009-04-06
Hi,
Coming straight to the point, is it possible in any way that we have different wallpapers for different desktops in Ubuntu 8.10
I have been trying but found nothing related that.
I think in Kubuntu, we can but in Ubuntu no idea.
Any suggestions?
I want to enjoy my Ubuntu a little bit more.

:popcorn:

---

### Post by gettinoriginal on 2009-04-06
Yes, there is.  You will need CompizConfig Settings Manager, if you don't have it, you can find it in synaptic.  Once installed it will be in System, Preferences, CompizConfig Settings Manager.  Open it, go to Utility, Wallpaper, make sure it is checked, then click on the icon to open it and choose choose Add to pick your wallpaper.  Add as many wallpapers as you have desktops.  

Once you have done that, close out the Settings Manager.  Now you will have to stop nautilus from drawing your desktop.  Alt F2 and enter ```
gconf-editor
``` > applications > nautilus > preferences > untick "show-desktop". 

Be aware however that once you do this, you will no longer be able to use desktop icons unless you go to Places, Desktop, and select them from there.

---

### Post by Naz_Farooq on 2009-04-06
> **gettinoriginal said:**
> Yes, there is.  You will need CompizConfig Settings Manager, if you don't have it, you can find it in synaptic.  Once installed it will be in System, Preferences, CompizConfig Settings Manager.  Open it, go to Utility, Wallpaper, make sure it is checked, then click on the icon to open it and choose choose Add to pick your wallpaper.  Add as many wallpapers as you have desktops.  

Once you have done that, close out the Settings Manager.  Now you will have to stop nautilus from drawing your desktop.  Alt F2 and enter ```
gconf-editor
``` > applications > nautilus > preferences > untick "show-desktop". 

Be aware however that once you do this, you will no longer be able to use desktop icons unless you go to Places, Desktop, and select them from there.

ok,
so will my changing wallpaper XML-wall work properly with this different desktop setting?

---

### Post by Naz_Farooq on 2009-04-06
Be aware however that once you do this, you will no longer be able to use desktop icons unless you go to Places, Desktop, and select them from there.[/QUOTE]

It means I cannot select other compiz setting as "cube"
& the other thing is that 3D effects will also work well or they will be disabled?

---

### Post by gettinoriginal on 2009-04-06
All of the compiz eye candy will still work, all you are doing is letting compiz control the wallpaper on each desktop, and taking it away from nautilus so icons will not show on the new "wallpaper".

---

