---
title: "Why are my menus so HUGE?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by sk545 on 2006-06-06
I mean, they are taking up like half of the desktop:

[http://tinypic.com/view/?pic=11uubra](http://tinypic.com/view/?pic=11uubra)

Can they be made smaller?  Everything seems kinda huge though....icons, menus, fonts (fonts aren't too bad, blurry, but i wound want them a little smaller on the desktop).

I installed nvidia drivers, and same thing happens...

Resolution: 1024x768
Refresh rate: 85hz
Monitor type: 19" CRT
Video card: 6600GT nvidia.
Nvidia driver version: 8762

Thanks, i don't want to change the resolution btw.

---

### Post by Jason_25 on 2006-06-06
That's normal.  Run 1280x1024 or 1600x1200 to make it look better.  Linux and mac  love high resolution.

---

### Post by ramcosca on 2006-06-06
That's exactly how it shows on my computer... :|

[QUOTE=Jason_25]That's normal.  Run 1280x1024 or 1600x1200 to make it look better.  Linux and mac  love high resolution.[/QUOTE]
Do I have to? I'm already having trouble reading stuff with 1024*768... :confused:

---

### Post by sk545 on 2006-06-06
> That's normal. Run 1280x1024 or 1600x1200 to make it look better. Linux and mac love high resolution.
I don't think one should HAVE to run it at that resolution.  But, sticking to the topic, is there no other way?

---

### Post by sk545 on 2006-06-11
^

---

### Post by elbryan on 2006-06-12
Mmh.. you could reduce the font of the menu (in kde you can do that configuring the Character Type Set).

I hate that huge menu that linux has.
For example, when I press "j" to jump to another song in xmms, the label on the window that appears are enormous :P

Try in this way..

---

### Post by chavo on 2006-06-12
Here's how to change your gtk icon sizes.

Create a file called .gtkrc-2.0 in your home directory and paste this in there 
```

gtk-icon-sizes = 
"panel-menu=16,16:
panel=16,16:
gtk-menu=16,16:
gtk-large-toolbar=16,16:
gtk-button=16,16"

```

You can make them whatever size you want. Just open the theme configuration dialog and toggle to a different theme and then back to make gnome aware of the changes.

---

### Post by ayoli on 2006-06-12
[QUOTE=elbryan]Mmh.. you could reduce the font of the menu (in kde you can do that configuring the Character Type Set).

I hate that huge menu that linux has.
For example, when I press "j" to jump to another song in xmms, the label on the window that appears are enormous :P

Try in this way..[/QUOTE]

xmms is gtk1.2, you can change gtk1.2 font by editing ~/.gtkrc and few lines such as:
```

style "font"
{
 font="-bitstream-dejavu sans-medium-r-normal-*-*-110-*-*-*-*-iso10646-1"
}
widget_class "*" style "font"
```
you can use xfontsel to select the font.

---

### Post by binos on 2006-06-13
An easier way is to lower the font sizes in System > Preferences > Font
I have them all on font size 9 with a resolution of 1024x768. Works for me.

---

### Post by alexmv on 2006-06-15
[QUOTE=Jason_25]That's normal.  Run 1280x1024 or 1600x1200 to make it look better.  Linux and mac  love high resolution.[/QUOTE]

What a wonderful solution. "and if you can't, run windows...". I always thought Linux was more flexible than windows but, maybe I was wrong :-(

---

### Post by jamesford on 2006-06-15
chavo, is there a way to make root apps also obey those icon sizes specified in .gtkrc-2.0 ?

---

