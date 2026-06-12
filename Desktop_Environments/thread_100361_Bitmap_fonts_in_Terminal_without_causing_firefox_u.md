---
title: "Bitmap fonts in Terminal without causing firefox ugliness"
date: 2005-12-07
forum: Desktop Environments
---

### Post by lecar_red on 2005-12-07
Hello Everyone,

I am trying to use bitmap fonts with gnome terminal. And enabling them with:

sudo dpkg-reconfigure fontconfig
 
And selecting the yes to the 'Enable bitmapped fonts by default?' works great, except it causes firefox's fonts to get ugly (incorrect kerning, fonts are degraded and look very incomplete.). 

When, I go back and choose 'no' for this option Firefox looks great but the Terminal has nearly unusable disable. I have tried to change the font settings in firefox after enabling the option but nothing looks as good as the default without bitmap fonts.

My question is how to I get bitmapped fonts for only the terminal? 

Thanks,

Lee

---

### Post by Strider420 on 2005-12-19
I was wondering if anyone has found a fix for this. I Am using the artwiz font package and can't stand the way firefox looks.

---

### Post by yamagami on 2006-01-01
I use the artwiz for the terminal, and although the Times font in Firefox seemd a bit odd after installing artwiz, it doesn't sound like its as bad as you describe. However, I did change the default font in firefox (preferences) to Verdana, which improved things quite a bit. Hope that works for you as well. 

Harel

---

### Post by 10drill on 2006-08-16
I've been having this problem today after enabling bitmap fonts (Artwiz) and found a few settings that helped me on the [Gentoo Wiki.]("http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts#Mozilla_Firefox_1.0.2B") Basically just making these changes got things looking good for me again:

In Firefox 1.5+, go to Edit » Preferences » Content » Fonts & Colors » Advanced.

Then, set these parameters: 
```

Proportional: Serif (Size: 16)
Serif: Bitstream vera serif
Sans-serif: Bitstream vera sans
Monospace: Bitstream vera sans mono (Size: 12)
Display Resolution: System setting
```

---

