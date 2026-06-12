---
title: "really small fonts"
date: 2006-08-29
forum: Desktop Environments
---

### Post by m.musashi on 2006-08-29
Among the many computer that I have installed dapper on is a newer dell latitude d820 with a 15.4 inch wide screen. The default resolution is 1920x1200. In dapper, this is quite small and I am constantly increasing font sizes in firefox to be able to see anything from the normal laptop distance. Although I don't have any options for other resolution via the screen resolution menu option (system -> preferences -> screen resolution) I'm not sure I want a different one. In windows, the other resolutions don't look very good at all.

Is there a way to change the default fonts for apps? I did find the font preferences option and changed all of them from size 10 to 12. Not a big change but I would have thought it at least noticable. Any bigger and things don't look good and it doesn't change web page fonts. I don't want to make everything ugly, just readable. Also, increasing font sizes tends to make pages not display right. A lower resolution would probably solve the problem but I don't think it will look as nice. Is this my only option or am I missing something.

Thanks

---

### Post by ubunick on 2006-08-30
I'd save yourself some time and just change resolutions.  Post a screenshot of the difference if you want.. it couldn't be that bad.

---

### Post by m.musashi on 2006-08-30
I was afraid that might be my only real option. However, since I do not have another other resolution options currently available, I assume I need to run the dpkg X11/xorg.conf, or what ever the command is, and add the other resoulution options. Doing that also runs me through keyboard setup and various other settings. Since I'd rather not inadvertantly change other settings, is there a way to change resoultions without the dpkg command?

---

### Post by CatKiller on 2006-08-31
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

Add the modes that you want, that your monitor supports, to the Modes line of the Monitor section.

---

### Post by m.musashi on 2006-08-31
Cool. Thanks. I'll do it that way and see how it goes. I wish there was a solution that allowed me to keep my best resolution but somehow have larger fonts that don't cause pages to look odd. Doesn't windows have an option for larger fonts?

---

### Post by danhm on 2006-08-31
Have you tried changing the defualt font size in Firefox?

Edit --> Preferences --> Content

---

### Post by m.musashi on 2006-08-31
I didn't set a new default as it seems you have to force pages to load that way otherwise they do what they want. If you force them, they usually don't look right. Instead, I've just been using the increase font option. It's an okay fix but as you get larger pages start to not display well and text starts to overlap. It seems you can you jump up one step and everything is nearly okay but still a bit off.

A different resolution is probably the easiest solution...just not one I'm real excited about.

Thanks for the input.

---

