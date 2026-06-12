---
title: "Applications Menu Icon"
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by DannyG on 2007-03-21
I've been at this for a while now and I can't seem to figure it out.

I want to change the icon next to the "Applications" menu to something else, and everything I've tried doesn't work.

I've changed "start-here.svg" and "distributor-icon.png"'s in several places but it never seems to change it.

Can someone help point me in the right direction? I am running Gnome on Edgy.

Thanks,
Daniel.

---

### Post by clutz2516 on 2007-03-21
I think your best bet would be to find the replacement icon in another theme, change it to what  you want and then apply the theme.  OR just find the icon in the theme that you are running, /usr/share/themes   I think this is what you mean.  Let me know how it goes! :)

---

### Post by DannyG on 2007-03-21
> **clutz2516 said:**
> I think your best bet would be to find the replacement icon in another theme, change it to what  you want and then apply the theme.  OR just find the icon in the theme that you are running, /usr/share/themes   I think this is what you mean.  Let me know how it goes! :)

I think you misunderstand.

I have the icon I want to change it to, and I'm using a theme I made myself.

I am just trying to change the icon, thats all. I know there is a file somewhere I need to change, but I don't know what the file is.

---

### Post by yt404 on 2007-04-04
did you ever find out how to solve this im working on it too in 6.10 and not having much luck

---

### Post by jlk on 2007-04-04
> I've changed "start-here.svg" and "distributor-icon.png"'s in several places but it never seems to change it.

I've not had any problems with Dapper/Edgy recognising .SVG changes.  I've just changed /usr/share/icons/your favorite theme/scalable/what ever and then do a 

```
killall gnome-panel
```

and the new icon appears.  Getting .PNG icons to appear needs a little more work.  You need to update the icon-theme.cache file.

```
sudo gtk-update-icon-cache –force /usr/share/icons/Human
```

replace 'Human' with the icon theme you are current using.

enjoy!

---

### Post by xopher on 2007-04-04
I just copy the distributor-logo.png file I want to ~/.icons/thethemeimusing/24x24/apps/distributor-logo.png

Works like a charm, just isn't consistent with theme changes, but gives the freedom to have different distributor-logo's for different themes ;)

---

### Post by diskotek on 2007-04-21
i couldn't find where is the application menu icon? (that ubuntu symbol...)
any ideas?

---

