---
title: "Change Web Browser Fonts in Ubuntu to Look Like Windows"
date: 2011-03-24
forum: Desktop Environments
---

### Post by Nipuna on 2011-03-24
Hello

You may Feel this as a Dump Question.  [IMG]http://www.expertcore.org/images/smilies/icon_e_smile.gif[/IMG] 

After  Buying a Router I have Internet connection to Ubuntu. I used to surf  the net using Ubuntu when I was using my Mobile to Get Internet. But  after Getting ADSL I switched to Windows because My Past Modem didn't  work with Ubuntu. So I bought a router.

Now My Problem is Ubuntu fonts are Smaller and bit different in Web Browsers. I have both Firefox and Cromium  in Ubuntu.

Now I want is to make Ubuntu Browser Fonts make similar to Windows 7 or Any Windows version.

I installed a Gnome Theme that Works like Windows 7 theme but it didn't change the Browser fonts so I removed it.

I think you Guys Help Me  [IMG]http://www.expertcore.org/images/smilies/icon_e_smile.gif[/IMG] 



Thanks

---

### Post by Frogs Hair on 2011-03-24
Find and install the fonts you want and from Firefox > Edit > Preferences > Content , select that font and apply. Opera and Chrome have similar settings for changing fonts. To change application fonts use appearance preferences fonts.

---

### Post by SeijiSensei on 2011-03-24
Try installing the MS "core fonts" using [this guide](http://helpdeskgeek.com/linux-tips/use-windows-fonts-in-ubuntu-linux/).  Once they're installed, you'll see old friends like Arial and Tahoma in your font lists.  For firefox, you'll need to specify the default with Edit > Preferences > Content.

---

### Post by Nipuna on 2011-03-24
Thanks friends

I tried this before I ask this Question by doing this

Edit > Preferences > Content   in all browsers.

But without installing windows fonts, I just Changed the fonts in browsers using fonts that come with Ubuntu but I couldn't do any difference. 

I know fonts of web sites are different from each other due to HTML coding.

I will try again and let you Know.

---

### Post by SeijiSensei on 2011-03-24
Most websites use "Cascading Style Sheets" to set fonts and many other layout features.  Well-designed stylesheets will request a series of fonts so that, if one isn't available, an alternative is tried.  Not surprisingly, most commercial sites design for Windows and often the developers don't think much, if at all, about how the site might render on other operating systems with the exception, perhaps, of Mac OS X.  A well-designed style sheet would have something like:

```

BODY     { font-family: Tahoma, Arial, Helvetica, sans-serif; }

```

You can tell Firefox to always use its own fonts in the Content dialog, but a better option is just to install the core fonts package.  Often that's all you need.

That said, font rendering in Windows will always be slightly different from rendering in Ubuntu or other Linux platforms.  Part of that has to do with intellectual property issues.  Many commercial fonts are "hinted" to improve the display (anti-aliasing issues, for example); Linux often can't follow those hints because it would require the installation of proprietary technologies that require licensing.

You can also try installing other browsers like Chrome or Opera or, if you're using Kubuntu, Konqueror or rekonq.

---

### Post by Old_Man_Unix on 2011-03-24
> **SeijiSensei said:**
> Try installing the MS "core fonts" using [this guide]("http://helpdeskgeek.com/linux-tips/use-windows-fonts-in-ubuntu-linux/").  Once they're installed, you'll see old friends like Arial and Tahoma in your font lists.  For firefox, you'll need to specify the default with Edit > Preferences > Content.

You already have the equivalent fonts in Ubuntu:

Times Roman -> Liberation Serif
Arial               -> Liberation Sans
Courier          ->  Liberation Mono

The only reason to use the MS fonts is  to meet legal or institutional requirements.

---

### Post by SeijiSensei on 2011-03-24
Trust me, those fonts don't look exactly like their Microsoft equivalents.  The reason I use MS fonts is so I can surmise how a page I've designed will look to the majority of visitors who'll be using IE on Windows.  Even then it's still something of a guessing game.

I guess that's an "institutional" requirement.

---

