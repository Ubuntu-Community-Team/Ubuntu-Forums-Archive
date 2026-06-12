---
title: "add the adobeRGB1998 profil in color setting in ubuntu"
date: 2016-06-02
forum: Desktop Environments
---

### Post by kaky951357 on 2016-06-02
hello everyone,
I am relatively new in the world of linux, i installed ubuntu in my new laptop a : asus x555la  i5 with an intel HD 5500 graphic ,after that i notice that the colors of display is kind of strange : the picture isn't realistic when i compared it to a external display that i plugged in VGA configured on adobeRGB1998 the difference was huge betwen them in terme of vivacity of colors , i go and check setting->color and i found that the integreted monitor is configured in less than sRGB in the CIE 1931 the triangle of colors that can be displayed is so small, i download the adobeRGB1998.icc try to add it to liste of profils that i can use it but its not working i probably did something wrong, and i came to ask for help to fixe my problem
thank you for trying to help me

---

### Post by mcduck on 2016-06-03
That sounds about right, that laptop definitely doesn't have the kind of display panel you'd need to show full sRGB range, let alone adobeRGB. Forcing it to use a color profile beyond it's capabilities won't give you more colors, it will just oversaturate the image and cause you to loose detail and accuracy.

The only profile you'd really want to use is one you get from a color calibrator. Assuming you don't have one available, the next best option is to use one provided by the manufacturer. And if there isn't one available, then using sRGB is the best you can do.
 You'll only usally see sRGB-capable display panels on higher end displays, and adobeRGB is pretty much limited to professional workstation displays.

---

### Post by kaky951357 on 2016-06-03
thank you for explanations 
i don't have the tools for calibrating  the screen, i search in a dababase icc profils i find some profils but the exacte refferece of my laptop don't match with the model they provide i teste it and its a lot beter than the defaults profil its bring a lot of vivacity to my screen, how can i force sRGB or other profils to compare it and use the best ?

---

### Post by mcduck on 2016-06-03
As far as I know, you'll get sRGB unless something else is specified, as it's the standard profile for desktop use (even though most panels can't actually display full sRGB color space).

Without a colorimeter or manufacturer profile I definitely would advice against trying anything else, especially if you ever do any kind of photo editing or graphics, as using wrong profile on your display would mean any images that look good on your computer will look completely different for everyone else. Of course if you don't do any of those things and just want brighter colors on your desktop, the easiest option would be to just see if your graphics drivers give you any controls for colors & saturation. But if you want to try different color profiles then you should be able to import one through the Color settings: [https://help.gnome.org/users/gnome-help/stable/color-howtoimport.html.en]("https://help.gnome.org/users/gnome-help/stable/color-howtoimport.html.en")

(most of the time if you see color profile making your colors more vivid, it means the profile is for use larger color space than what your display can handle, and you actually loose most of the colors by using such profile. The only exception being wide-gamut professional displays that actually go beyond the sRGB color space, but those are pretty rare outside of professional workstations and also are quite expensive.)

---

### Post by kaky951357 on 2016-06-04
hello 
i don't do any kind of editing i'm juste a simple user, the problem is that when i wish to try a new profile it dosn't want to appear in the liste "add profile" the only profiles that i can correctly setup is these that are provided for other asus laptops ven if i apply exactly what they said in : [COLOR=#000000] [/COLOR][https://help.gnome.org/users/gnome-h...import.html.en]("https://help.gnome.org/users/gnome-help/stable/color-howtoimport.html.en") , i can see the profiles that i impor in "color profile viewer" but impossible to use them.
[COLOR=#000000]"the easiest option would be to just see if your graphics drivers give you any controls for colors & saturation": how can i now if my drivers give me control ?[/COLOR]

---

