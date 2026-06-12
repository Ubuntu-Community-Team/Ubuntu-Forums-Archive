---
title: "Fonts rendering in Ubuntu (better &quot;ClearType&quot; look ?)"
date: 2006-01-20
forum: Desktop Environments
---

### Post by frontline3k on 2006-01-20
Hi.
I know you guys don't like Suse, but ... in SUSE 10.0 I found a desktop look I can't recreate in Ubuntu. Specially I'm talking about fonts and fonts rendering.
It's the closest look to "Clear Type", which looks nice on LCD screens (like mine, on both machines I use for current works (desktop and laptop)).
For a self-explanatory view of what I'm talking about, please look at the picture below.

I "almost know" some info:
1. The font is "Sans Serif" - I don't know which one, I can't find it in Suse (hints about identifying the files u ?)
2. Resolution is 75 dpi (changed that, recreate the fonts cache, restarted X .... no results ... fonts looks preety ugly).
3. .fonts.conf from Suse looks like this
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
</fontconfig>
```
Tried the same config in Ubuntu ... I can't see the difference.

Fonts rendering is related to desktop manager (KDE - default in SUSE / Gnome - default in Ubuntu) or to Xorg ?
I'm almost sure I can mimic this in any Linux distro ... don't know how.

Also, the whole X seems to be faster in SUSE than Ubuntu (and I'm talking about running these distros on the exact same machine). Hints ?

For any other info you need to complete the picture, please ask.

Regards,
frontline3k

---

### Post by tmahmood on 2006-01-20
Have you tried System>Preference>Fonts ?

select Subpixel Smoothing...

---

### Post by frontline3k on 2006-01-20
Yep.
Another ideea ?

---

### Post by obibok on 2006-01-23
I've just noticed my favourite question :) - Replying! ...well, after 3 days but with all the forum problems lately...

[http://linuxtuneup.blogspot.com/2005/11/fonts-better-than-cleartype.html](http://linuxtuneup.blogspot.com/2005/11/fonts-better-than-cleartype.html)

---

