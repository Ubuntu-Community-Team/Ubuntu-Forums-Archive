---
title: "Cannot restore subpixel settings"
date: 2009-06-05
forum: Desktop Environments
---

### Post by etienne@Rofti on 2009-06-05
Hi! I use a few KDE applications, and when I changed my Gnome appearance theme, I opened up KDE4's System Settings to change the theme of my KDE apps as well to fit with my new GTK theme.

However, I fiddled around a bit with my font subpixel settings, and now those settings have been applied system-wide. No matter what I do in Gnome appearance settings, I am unable to change it back!

Anyone who knows how to disable the hold that KDE has over my Gnome appearance settings?

Thanks!

---

### Post by etienne@Rofti on 2009-06-05
Please can someone help? Here is my fonts.config:

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="embeddedbitmap" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <test compare="more_eq" name="size" qual="any" >
   <double>8</double>
  </test>
  <test compare="less_eq" name="size" qual="any" >
   <double>15</double>
  </test>
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <test compare="more_eq" name="pixelsize" qual="any" >
   <double>11</double>
  </test>
  <test compare="less_eq" name="pixelsize" qual="any" >
   <double>20</double>
  </test>
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>
```

---

