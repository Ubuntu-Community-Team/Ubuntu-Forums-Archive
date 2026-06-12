---
title: "Unhappy with text rendering in Ubuntu"
date: 2008-12-30
forum: General Help
---

### Post by KeilanS on 2008-12-30
Hey everyone,

I've found the font in Ubuntu looks very wispy and blockish when compared to what I'm used to with Windows Vista. I googled it and found a fix which involved making a file called ".fonts.conf" in my home/user directory. But that did not make any noticeable difference. Is there another fix, or does anyone have any thoughts on what I may have done wrong?

Here is the code that I placed in the text file. Also, in case this is note worthy, the text file is not displaying as text, it is displaying as an icon that looks like a text file with a planet on it (I think that is because it is a .conf file).

```
&#8722;
<fontconfig>
&#8722;
<match target="font">
&#8722;
<edit mode="assign" name="autohint">
<bool>true</bool>
</edit>
</match>
&#8722;
<match target="font">
&#8722;
<edit mode="assign" name="rgba">
<const>none</const>
</edit>
</match>
&#8722;
<match target="font">
&#8722;
<edit mode="assign" name="hinting">
<bool>false</bool>
</edit>
</match>
&#8722;
<match target="font">
&#8722;
<edit mode="assign" name="hintstyle">
<const>hintnone</const>
</edit>
</match>
&#8722;
<match target="font">
&#8722;
<edit mode="assign" name="antialias">
<bool>true</bool>
</edit>
</match>
</fontconfig>
```

---

### Post by nikgare on 2008-12-30
I have turned off hinting in via the appearence prefernce dialogue box - it's the only way I've found to get nice looking fonts in Linux.

---

### Post by Bachstelze on 2008-12-30
My $0.02: switch to KDE. :D

Don't my fonts look fabulous?

---

### Post by Seks on 2008-12-30
They look fine to me as default in gnome (intrepid). Are you using your monitors native resolution? Not doing so can make them look horrendous.

---

### Post by scorp123 on 2008-12-30
> **HymnToLife said:**
> Don't my fonts look fabulous? I fail to see a difference with what I have on GNOME here.

I second what another poster a bit further up said ... Having the wrong refresh rates, wrong color depth and wrong resolution on one's screen can cause the fonts getting rendered way uglier than they should be. I once had a Nvidia FX5000-odd-something card and for some really silly reasons X11 would report that I only had "60 dpi" despite having a 1280x1024 screen resolution ... my fonts looked abysmal.

What I would suggest is to use **xdpyinfo** and check what it reports regarding the "dots per inch". If I do that on my system I get (irrelevant parts skipped): 
```
 > xdpyinfo  | more
(... skipped ...)
screen #0:
  dimensions:    2680x1050 pixels (792x310 millimeters)
  [COLOR="Red"]resolution:    **86x86 dots per inch**[/COLOR]
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x13b
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
(... skipped ...)
``` So my screen reports having 86 dpi and fonts look tip top. Below 72 dpi fonts start looking bad, and at around 60 dpi they really do look kinda ugly. At around ~90 dpi fonts should look sharp and clear, beyond 100 dpi they maybe will start looking small, so you maybe will have to use fonts made for 100dpi and beyond.

IMHO it's worth checking what dpi gets reported back by the system. There are various ways (e.g. parameters one could place into /etc/X11/xorg.conf) to force the system to use a specific dpi resolution .... with modern graphics cards you shouldn't have to do this though, but still ....

---

### Post by Bachstelze on 2008-12-30
> **scorp123 said:**
> I fail to see a difference with what I have on GNOME here.

Well, well, when I use GTK apps here, the fonts do look absolutely ugly.

---

### Post by scorp123 on 2008-12-30
> **HymnToLife said:**
> Well, well, when I use GTK apps here, the fonts do look absolutely ugly. Screenshot please? And a screenshot showing your font settings (from the "Appearance" menu)? Would be interesting to compare it side by side with the KDE screenshot above (I honestly mean that).

---

### Post by Zorael on 2008-12-30
I don't get a huge difference between Qt4 and GTK apps on my system, after having put some effort into configuring it. See attachment.

(Konqueror is bleh at drawing web pages >.<)

---

### Post by KeilanS on 2008-12-30
Hey everyone,

My monitor is running at it's native Resolution (1280 x 800) and is reporting 112 dpi in the xdpyinfo.

I turned off hinting but that didn't make a noticeable difference. Maybe it's all in my head. Next time I'm in Vista I'll pay more attention.

---

### Post by oldos2er on 2008-12-30
If you're using an LCD monitor, check System, Preferences, Appearance, Fonts, enable subpixel smoothing; click Details, check subpixel (I don't know why this option is there twice), and full hinting.

---

