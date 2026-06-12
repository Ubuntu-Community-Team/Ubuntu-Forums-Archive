---
title: "gdm - change login screen fonts"
date: 2009-01-11
forum: Desktop Environments
---

### Post by cjns1989 on 2009-01-11
I'm trying to change the default font on the "Human" login screen of ubuntu 8.10.

I first looked in the "admin > login screen" popup and didn't find anything suitable.

I proceeded to clone the "Human" theme in /usr/share/gdm/themes and edited the "Human.xml" file, replacing all occurrences of "Sans" by "Verdana" and changed the font size to "8" instead of "11". This last point is important - see below.

I also edited the "Greeter" file in the same directory so that it would reflect my "new" theme name instead of "Human" and selected the new theme by running "admin > login screen".

I logged out of my session and was presented with a modified "Human" login screen where the fonts were smaller as requested (changing them was one simple way of checking that it was indeed my modified version of "Human" that was selected) but the font itself was definitely not Verdana. As far as I know, it was still the default "Sans" that I was trying to replace.

I googled quite a bit and found many posts where other users were trying to change the size of their fonts but nothing relative to the font itself. 

Since desktop fonts, gtk fonts, browser content fonts, etc. were immediately changed to Verdana when I used the various font customization GUI's, I suspect that everything in the current ubuntu/gnome environment is handled by asking fontconfig for the specified font and likewise I'm beginning to suspect that gdm does not use fontconfig (despite the xml-ization of its configuration files).

Since gdm runs under the "root" user, I tried another approach where I temporarily authorized the superuser to log on, added a "root" user (useradd + passwd root) .. logged as root to a gnome desktop (!) and customized the desktop fonts to my liking (verdana 8, hinting=medium, antialiasing=off) via the "preferences > appearance > fonts" popup and although root's desktop was precisely what I had required, the gdm logon screen still had the same font that looks quite different from Microsoft's Verdana.

Has anyone had any luck with this?

Thanks!

CJ

---

### Post by Mazin on 2009-01-11
The GDM login themes are explicitly controlled by the theme files, i.e. you were right to look there.

However, changing the font in Human.xml works perfectly for me.  I did a ```
s/Verdana/CrimeFighter BB/g
``` (10 occurrences replaced).

To quickly test if your new theme works, go into a console and type
```
gdmthemetester console Human
```
and an Xnest window will pop up with your current theme.  It could be that the system cannot find "Verdana"; does changing Sans to something like "Corbel" or "Bitstream Charter" do anything?

---

### Post by cjns1989 on 2009-01-11
Since it definitely looks like it's not able to find Verdana, I thought about switching to another font but had to attend to other matters.

Thanks also for the theme tester .. I'm now in debian etch but will reboot shortly.

CJ

---

### Post by Mazin on 2009-01-11
Oh, I forgot.  Is the font you want in your user fonts (i.e. in ~/.fonts)?  I would imagine that only system-wide fonts would be usable by GDM.

---

### Post by cjns1989 on 2009-01-11
> **Mazin said:**
> Oh, I forgot.  Is the font you want in your user fonts (i.e. in ~/.fonts)?  I would imagine that only system-wide fonts would be usable by GDM.

Thanks!

Actually, I tried in succession "Terminus 8" .. "Georgia 8" .. "Trebuchet 8" and then again "Verdana 8" and I realized that each time I was getting the font I requested. 

The reason I did not recognize Verdana 8 originally is that there appears to be some default antialiasing on the gdm login page, that makes all fonts look like pea soup at such sizes.. difficult to recognize & almost illegible.

That's why I experimented with serif fonts a bit so that I could tell them apart from a non serif font such as Sans or Verdana.

Wonder if anyone knows how I can turn that antialiasing off. at least for small fonts..?? I wasn't able to find any samples.. or a document that describes the syntax of the "theme_name.xml" file.

Another problem is that my changes only affected the login screen page per se: the "Options" menu (bottom left of the screen in the Human theme) is stuck with the "Sans" default font. I have no clue where I could change the font for that.

If anyone is familiar with ubuntu's bug/feature request system, I think it would be worth pointing out to the developers that having to edit files (whose syntax appears not to be documented anywhere..) .. especially .xml files .. goes a bit against the grain of ubuntu and that they might consider adding a "fonts" tab to the "admin > login screen" popup that would let you specify the fonts you want to use, the size of the fonts, and what kind of smoothing/hinting you would prefer rather than having to go through these contortions. 

Anyway, I'm not going to go crazy over this.. if anyone has ideas re: antialising (getting rid of it) or how to change the font on the options menu, I would much appreciate .. otherwise I'll just have to live with it.

Thanks much for your patience and all your help!

CJ

---

