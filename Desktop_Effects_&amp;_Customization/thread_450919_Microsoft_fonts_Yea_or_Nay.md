---
title: "Microsoft fonts: Yea or Nay?"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by skip27 on 2007-05-21
I've been using Ubuntu for the past 5 months, with everything going exceptionally well except for one thing: font rendering. In OpenOffice.org, particularly, I've struggled to get the fonts to render the way I want them to, adjusting everything from the .fonts.conf file to downloading the Turner freetype/cairo libraries. Even outside of ooo, I noticed that Microsoft fonts did not render the way they would in Windows, and I was oftentimes disappointed with the quality.

Many documents I use were typed in Arial, Times New Roman, etc. much to my disappointment, and I always felt that they just didn't look right in Linux. I nearly switched back to Windows, except I decided to try one last thing (the MOST obvious thing): why not just NOT install the MS fonts?

And now? My documents look gorgeous in ooo using the standard Ubuntu fonts, and now I am wondering, why should I use Microsoft fonts? Sure, plenty of websites are done in Arial (like CNN.com), but they look even better (in my opinion) in Bitstream Vera than in Arial. ooo does an excellent job at font substitution, and now I don't have to struggle with getting freetype to render MS fonts "properly."

How many of you have said to hell with Microsoft and just used the standard fonts? It's almost like Microsoft doesn't want their fonts to render properly on any other platform... Or, if you take the opposing side, how did you get the MS fonts to render cleanly on Ubuntu, or did you simply just settle with the quality you got? To be frank, I wasn't even really happy with Microsoft's job at rendering their own Times New Roman in Windows, nevermind Linux.

---

### Post by reclusivemonkey on 2007-05-22
The only place I use MS fonts is in my accounts spreadsheet which I open and edit both at home and work.

---

### Post by Kobalt on 2007-05-22
I don't use them in Ubuntu. If I need to pass on a document I'd rather use either pdf if I want the formating not to change, or OpenOffice documents (.odt or .doc).

---

### Post by skip27 on 2007-05-23
I've probably spent way too long experimenting with just fonts, but tonight, I spent a good amount of time just playing around with settings and reinstalling the MS fonts. What's unfortunate is that even though I may be able to enable the bytecode interpreter in the freetype libraries, I won't ever be able to get them to work with OpenOffice for one reason or another; I even tried recompiling OpenOffice.org with the Turner BCI-enabled libraries, but to no avail. But, that's not it. Even if I do manage to enable the BCI, the MS fonts still don't render properly (e.g. the letters are too spaced out using full subpixel hinting, and as a result, some of the letters get cut off). Sure, I can use "slight" subpixel hinting, but then the quality goes down substantially.

So, it seems that regardless of what option I take, I have to make some kind of a compromise. So, I've decided to reinstall the MS core fonts, but now I do not use the Turner libraries; I just use the freetype/cairo libraries that come with Ubuntu. Not only do I now have uniform font rendering across the system (like with OpenOffice.org), but I think I've come to a reasonable compromise to where I can enjoy many fonts with decent rendering.

EDIT: Ubuntu does come with the BCI enabled, much to my surprise. Since mp3 support doesn't even come with it by default, I thought that it was even less likely that the BCI would as well. I tried compiling Freetype 2.1.10--the version that is guaranteed to work completely with ooo--without the BCI (ftoption.h) and then using LD_PRELOAD to use it with the version of ooo that I compled, and lo and behold, I had blurry fonts. THEREFORE, in Feisty at least (not sure about Edgy), I know for certain that the BCI does come compiled into ooo and the system itself uses Freetype libraries that have the BCI enabled.

Clearly, at this point, I'm still ambivalent about using the MS fonts; they still bug me to an extent. Anyway, I thought I'd just share my two cents just in case someone who was curious about this can read my personal experiences.

---

### Post by stchman on 2007-05-23
> **skip27 said:**
> I've been using Ubuntu for the past 5 months, with everything going exceptionally well except for one thing: font rendering. In OpenOffice.org, particularly, I've struggled to get the fonts to render the way I want them to, adjusting everything from the .fonts.conf file to downloading the Turner freetype/cairo libraries. Even outside of ooo, I noticed that Microsoft fonts did not render the way they would in Windows, and I was oftentimes disappointed with the quality.

Many documents I use were typed in Arial, Times New Roman, etc. much to my disappointment, and I always felt that they just didn't look right in Linux. I nearly switched back to Windows, except I decided to try one last thing (the MOST obvious thing): why not just NOT install the MS fonts?

And now? My documents look gorgeous in ooo using the standard Ubuntu fonts, and now I am wondering, why should I use Microsoft fonts? Sure, plenty of websites are done in Arial (like CNN.com), but they look even better (in my opinion) in Bitstream Vera than in Arial. ooo does an excellent job at font substitution, and now I don't have to struggle with getting freetype to render MS fonts "properly."

How many of you have said to hell with Microsoft and just used the standard fonts? It's almost like Microsoft doesn't want their fonts to render properly on any other platform... Or, if you take the opposing side, how did you get the MS fonts to render cleanly on Ubuntu, or did you simply just settle with the quality you got? To be frank, I wasn't even really happy with Microsoft's job at rendering their own Times New Roman in Windows, nevermind Linux.

I really like Ubuntu and use it pretty much 100% of the time now.  I also agree that Ubuntu has way worse fonts than XP.  I did however discover a gentleman on here that was able to give Ubuntu that XP look in the fonts department.  If you want this then use the procedure I wrote up based on his work.

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

Looks as good as XP and you don't need to deal with M$.

If you are trying to get fonts in OO2 in Edgy or OO2.2 that you download from OO's website I have tried every way I know how.  There is good news though.  OO2.2 installed with Feisty has beautiful fonts.

---

### Post by oomingmak on 2007-05-23
I have a subset of the msttcorefont set installed, but they are not currently being used.

The one font that I do use (as my main system font) is Segoe UI.

---

### Post by ronocdh on 2007-05-23
Man, I don't mean to be a jerk, but I always thought XP's handling of fonts was abysmal. Even Ubuntu's was a little prettier, except in the case of a low-quality PDF or something. I've certainly never been driven to switch back to MS fonts!

---

### Post by stchman on 2007-05-23
> **ronocdh said:**
> Man, I don't mean to be a jerk, but I always thought XP's handling of fonts was abysmal. Even Ubuntu's was a little prettier, except in the case of a low-quality PDF or something. I've certainly never been driven to switch back to MS fonts!

Download and use the script to kill the AA of the fonts.  IMO Ubuntu uses way to much AA on fonts.

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

Try it.  You can always remove the scripts.

---

### Post by skip27 on 2007-05-24
> **stchman said:**
> Download and use the script to kill the AA of the fonts.  IMO Ubuntu uses way to much AA on fonts.

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

Try it.  You can always remove the scripts.

Thanks for posting that, but that is one of the many things I have already tried. I don't like the fact that I have to compromise antialiasing just because I use Linux. Furthermore, even with the tailored font configuration files, it still doesn't change the fact certain MS fonts, like Times New Roman, don't render correctly under certain circumstances. For example, the italicized letter 'z' looks bad, and if memory serves, the font configuration files provided above allow aliasing for italic fonts. The problem here is that the middle portion of the letter 'z', when italicized, doesn't even show up. I'm willing to bet anything that MS has done something to the fonts that cause them to render properly only under a Windows configuration; it obviously has something to do with the hinting.

I also tried disabling aliasing without using any font configuration files, but then the italicized fonts appeared jagged and ugly. Or, in other words, I used the MS fonts with the Monochrome option in the Gnome Font control panel. So, as of now, I am using NO Microsoft fonts and have LCD subpixel rendering at full. Everything is just peachy. I have uninstalled the enhanced Turner libraries so I have uniform font rendering across my system, and now I'm completely happy.

---

### Post by stchman on 2007-05-24
> **skip27 said:**
> Thanks for posting that, but that is one of the many things I have already tried. I don't like the fact that I have to compromise antialiasing just because I use Linux. Furthermore, even with the tailored font configuration files, it still doesn't change the fact certain MS fonts, like Times New Roman, don't render correctly under certain circumstances. For example, the italicized letter 'z' looks bad, and if memory serves, the font configuration files provided above allow aliasing for italic fonts. The problem here is that the middle portion of the letter 'z', when italicized, doesn't even show up. I'm willing to bet anything that MS has done something to the fonts that cause them to render properly only under a Windows configuration; it obviously has something to do with the hinting.

I also tried disabling aliasing without using any font configuration files, but then the italicized fonts appeared jagged and ugly. Or, in other words, I used the MS fonts with the Monochrome option in the Gnome Font control panel. So, as of now, I am using NO Microsoft fonts and have LCD subpixel rendering at full. Everything is just peachy. I have uninstalled the enhanced Turner libraries so I have uniform font rendering across my system, and now I'm completely happy.

I guess this is where we differ in opinions.  I think the scripts make Ubuntu look way better in the fonts department.

Everyone has different tastes.

---

