---
title: "Turning off antialiasing for Tahoma font"
date: 2005-12-28
forum: Desktop Environments
---

### Post by jdreilly on 2005-12-28
My default ubuntu fonts look ok with anti-aliasing enabled and terrible when its disabled. However I prefer to use Tahoma, size 8, for my desktop and application fonts as it looks better on my laptop screen. But it looks crap when anti-aliasing is enabled and great when it's disabled. So in an ideal world, what I'd like to see is anti-aliasing on by default, but disabled for the Tahoma font.

Unfortunately, the Gnome font preference editor doesn't provide the fine-grained control to disable anti-aliasing for Tahoma only, so I've created a ".fonts.conf" and dropped it my home directory (see below). It basically turns off anti-aliasing for all fonts below 10-point. But for some reason it's not having any effect. Can anyone suggest a reason why? Or perhaps there is another way of going about this? 

Cheers

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- ~/.fonts.conf for per-user font configuration -->
<fontconfig>

<!--
        Private font directory
-->
<dir>~/.fonts</dir>

<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>0</double>
 </test>
 <test compare="less" name="pixelsize" qual="any">
  <double>10</double>
 </test>
 <edit mode="assign" name="antialias">
  <bool>false</bool>
 </edit>
</match>
</fontconfig>

---

### Post by dcstar on 2005-12-28
[QUOTE=jdreilly]My default ubuntu fonts look ok with anti-aliasing enabled and terrible when its disabled. However I prefer to use Tahoma, size 8, for my desktop and application fonts as it looks better on my laptop screen. But it looks crap when anti-aliasing is enabled and great when it's disabled. So in an ideal world, what I'd like to see is anti-aliasing on by default, but disabled for the Tahoma font.

Unfortunately, the Gnome font preference editor doesn't provide the fine-grained control to disable anti-aliasing for Tahoma only, so I've created a ".fonts.conf" and dropped it my home directory (see below). It basically turns off anti-aliasing for all fonts below 10-point. But for some reason it's not having any effect. Can anyone suggest a reason why? Or perhaps there is another way of going about this? 
.......[/QUOTE]
Have a look at this thread, it may be helpful:

[http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)

---

