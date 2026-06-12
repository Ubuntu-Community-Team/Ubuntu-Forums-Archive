---
title: "&quot;Live&quot; change of subpixel order with LXDE"
date: 2011-03-27
forum: Desktop Environments
---

### Post by tupfzom on 2011-03-27
I have a pivot screen that I frequently switch between portrait and landscape mode.  With

```

xrandr -o normal

```

and

```

xrandr -o left

```

I can rotate the display.  I used to change the subpixel order with

```

gconftool-2 -s /desktop/gnome/font_rendering/rgba_order -t string "rgb"

```

and

```

gconftool-2 -s /desktop/gnome/font_rendering/rgba_order -t string "vrgb"

```

when I used Gnome, but this is not working with my current setup.  I'm using Maverick 32bit with LXDE now.  Gconf is installed and obviously running (at least "lsof | grep gconf" prints quite a number of lines).  But even applications that obviously rely on Gconf (like Gedit) don't change their font rendering, even if I restart them.

I can change the subpixel order in my ~/.fonts.conf

```

...
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 ...
</fontconfig>

```

and when I restart programs, they use the proper subpixel order for font rendering.  However, I'd like to avoid having to close and restart all running applications.  I find that subpixel antialiasing/hinting greatly improves readability, but of course text that's rendered using the wrong subpixel order is totally irritating.

Is it possible to somehow put Gconf in charge so the font rendering changes "live" like in Gnome?  Or is there another way of getting the same effect with fontconfig or something?

Thanks!
Thomas W.

---

### Post by tupfzom on 2011-03-30
Sorry for bumping, but doesn't anyone know how to make gconf responsible for changing font rendering parameters outside Gnome?

---

