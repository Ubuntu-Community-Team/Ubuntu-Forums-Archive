---
title: "Ugly font in firefox"
date: 2008-11-08
forum: Desktop Environments
---

### Post by sionghua on 2008-11-08
The fonts in firefox appear ugly, is there a way to improve it? I think may be it needs some smoothing etc...

---

### Post by blackened on 2008-11-08
```
sudo apt-get install msttcorefonts
```

Also check what your default font is under Edit->Preferences->Content Tab. This is the font that firefox will use if the page doesn't specify one.

---

### Post by sionghua on 2008-11-08
found the solution, went to system, appearance - fonts - subpixel smoothing, then restart firefox.

---

### Post by bapoumba on 2008-11-08
Moved to Desktop Environments.

---

### Post by theduffman on 2008-11-08
for me, ive found the msfonts do a poor job on some sites, so ive set FF to use FreeSans/FreeSerif/FreeMono, looks a lot better imo, ive also set them for desktop too..

---

### Post by Yashiro on 2008-11-08
Get 'Droid' and Macfonts.

---

### Post by blackened on 2008-11-08
> **Yashiro said:**
> Get 'Droid' and Macfonts.

I tried Droid for a while, but it never seems to look as good as bitstream vera sans. 

Does libfreetype come compiled with truetype bci in ubuntu?

---

### Post by Yashiro on 2008-11-09
RGBA Droid with slight hinting looks really good here. Almost on par with my Mac.

---

### Post by sionghua on 2008-11-09
firefox now looks fine, however openoffice seems to ignore subpixel smoothing in its UI.

---

### Post by theduffman on 2008-11-10
> **sionghua said:**
> firefox now looks fine, however openoffice seems to ignore subpixel smoothing in its UI.

gedit ~/.fonts.conf

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintnone</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

try that

---

### Post by sionghua on 2008-11-10
Thanks, tried that but still the same, it's OO 3.0 here.

---

### Post by theduffman on 2008-11-12
> **sionghua said:**
> Thanks, tried that but still the same, it's OO 3.0 here.

well thats how ive got fonts configured and i think its looks ok..
try those, font sizes are your own choice, depending on screen size etc..  oo2 default 8.10 here btw

---

