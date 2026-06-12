---
title: "kde 4.3.2 multiple wallpapers (exists?)"
date: 2009-10-27
forum: Desktop Environments
---

### Post by Ajat on 2009-10-27
Hi i've seen the KDE 4.3.0 released page here [http://www.kde.org/announcements/4.3/index.php](http://www.kde.org/announcements/4.3/index.php) , the demo video there is just awesome...

they said that now plasma and kwin are integrated, but it seems that it is not the case in KDE 4.3.2, as now i can't choose different wallpaper and widget for each desktop.

is there any explaination for this?

---

### Post by jacksaff on 2009-10-27
The capability is there but the gui for it is still awful (there's a new one coming).
You need to click zoom out on the cashew thingy and then the option to have different wallpapers for each desktop is in the 'configure plasma' menu there...

---

### Post by jtappin on 2009-10-27
> **jacksaff said:**
> 
You need to click zoom out on the cashew thingy and then the option to have different wallpapers for each desktop is in the 'configure plasma' menu there...

Strictly it's "Different Activity for each desktop". Then you have to go to each Desktop/Activity in turn and set the wallpaper by right clicking on the desktop and selecting "Desktop settings"

I agree though it's seriously clunky -- in fact I found it by accident on my Karmic test box and then forgot and couldn't find it on my Jaunty+PPA mainstream boxes for a few days.

---

### Post by Ajat on 2009-10-28
guys, i dont know what happen to my plasma..
everytimes i change the wallpaper of a specific desktop.. it also changes the wallpaper on the other desktops. 

and also the widgets can't be different for each desktop.

perhaps can you lend me the  plasma-desktop-appletsrc files ..

---

### Post by Ajat on 2009-10-28
I found it.. the configure plasma, show up after i kill plasma-desktop and add 
```

[Global] 
perVirtualDesktopViews=true

```

to plasma-desktoprc and/or plasmarc (i dont know which one does the job)

thanks.

---

