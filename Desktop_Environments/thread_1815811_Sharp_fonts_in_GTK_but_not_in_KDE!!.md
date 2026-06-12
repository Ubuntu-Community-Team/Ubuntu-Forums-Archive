---
title: "Sharp fonts in GTK but not in KDE!!"
date: 2011-08-01
forum: Desktop Environments
---

### Post by adank92 on 2011-08-01
I used the .font.conf from [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) and its working great for Pidgin, firefox and programs GTK based but is not working in the whole KDE system. How can i make the KDE Sharp as in GTK?

[[IMG=http://img8.imageshack.us/img8/1553/instantnea1c.png][/IMG]]("http://imageshack.us/photo/my-images/8/instantnea1c.png/")


Thanks!

---

### Post by Ms_Angel_D on 2011-08-01
Hi adank92,

Try saving the following in a file in your home directory called .fonts.conf

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font">
  <edit mode="assign" name="autohint">
   <bool>true</bool>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="rgba">
   <const>none</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="hintstyle">
   <const>hintnone</const>
  </edit>
 </match>
 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>
```

then run the command 
```
sudo fc-cache -f -v
```

I'm using it on my own Kubuntu and it works great the font looks pretty good. So I Hope this helps you.

Angel

---

### Post by adank92 on 2011-08-01
Thanks for the reply! I used your .font.conf but it looks very blury too. I want to get it sharp like in Windows XP (i can read better with that font style), i used TAHOMA for all fonts and the .font.conf from [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) but it looks sharp only in GTK programs like Firefox, pidgin.. How can i get KDE to render like those? (see picture above)

THANKS!

---

### Post by Ms_Angel_D on 2011-08-01
hmm try opening KDE system settings and going to

Application Appearance -> Fonts

and changing force fonts DPI to 96 DPI or 120 DPI you might also want to try enabling anti-aliasing the clicking configure and and checking use sub-pixel rendering RGB and see if that helps any.

---

### Post by adank92 on 2011-08-01
I tried with 96 and 120 DPI, but it looks the same, i tried a bunch of different combinations but i dont understand why is working in GTK and not in the whole KDE system.

See the difference between the sharp firefox and the blurry KDE.
[http://img594.imageshack.us/img594/882/instantnea2v.png](http://img594.imageshack.us/img594/882/instantnea2v.png)

Thanks!!

---

### Post by Ms_Angel_D on 2011-08-01
In all honesty I don't see the difference in the picture they both look pretty clear to me. Actually if anything I would say the font on the webpage looks blurry but the rest looks pretty clear.

The only other thing I could recommend is going to kde system settings -> application appearance -> GTK+ Appearance and making sure you have QtCurve selected as the widget style and checked "use my kde fonts in GTK+ applications"

or you could try messing with those settings.

But honestly in the photo your font's just don't look blurry to me.

---

