---
title: "konsole fixed font is ugly, xterm is fine"
date: 2006-10-10
forum: Desktop Environments
---

### Post by cma on 2006-10-10
I am having a really hard time getting konsole to look normal.  XTerm is fine though.  I've tried dpkg-reconfigure fontconfig and making a fonts.alias file.  The font is obviously there, but why can't konqueror see it?

---

### Post by kerry_s on 2006-10-10
You could try changing the font size>settings>font> enlarge font.
save as default to keep.

You can also check in kcontrol to see if you got subpixel hinting turned on and if it's set to full.

Why does your pic look so crappy?

Here's what my terms look like, i only increased the font(bad eye's)->

---

### Post by cma on 2006-10-10
Sorry, I should have been more specific on that.  When I try to change the font size on konsole, I can use 8, which is what you see in the image, or 10, which looks terrible.  For some reason, konsole (and I assume KDE) doesn't see the encoding from the xfontsel, which is strange because xterm does fine.

Here's what I get when trying to change the font in konsole.  I've lowered the color depth to reduce the image size.

---

### Post by kerry_s on 2006-10-10
I would check in kcontrol and see what the fixed fonts are set to, i think kcontrol overrides fontsel. I don't have that many font's installed on mine, but here's what mine look like.->

---

### Post by cma on 2006-10-10
Even in kcontrol, I get the same thing.  I can have huge fixed that looks ok (size 11), tiny that looks squished (size 8 ) or size 10 which looks too wide and fuzzy.  I haven't poked around with other fonts, as they are generally ok.

I'm wondering if it has something to do with iso-8859-1 vs. utf8 encoding.  If I select 10 and do italic or bold, it looks good, with the obvious respective exceptions.  xfontsel can see the font as I would like it, so it does exist on the system.

---

### Post by pau on 2007-10-28
Why don't you try to add something like this to your /home/username/.fonts.conf ? 

It should work. Let me know whether you have problems. No reconf needed; should work "out of the box", as a lot of people say here.

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
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

That should make it. Let me know.

Pau

---

### Post by pau on 2007-10-28
Ooops... I realise only now that this was one year ago... Anyway, I hope you read this

---

