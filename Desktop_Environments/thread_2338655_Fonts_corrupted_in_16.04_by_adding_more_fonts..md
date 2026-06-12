---
title: "Fonts corrupted in 16.04 by adding more fonts."
date: 2016-09-30
forum: Desktop Environments
---

### Post by lukon on 2016-09-30
I added more fonts (ttf type) to my 16.04 system. Now some programs (LibreOffice, some web pages) use one of the new fonts without authorization. Manually picking the correct font only fixes the problem for the current program session. Restarting the program puts the unwanted font back. At least it is consistent about it, picking the same new unwanted font each time. But It is not a very readable font at the scale it gets used.

The only cure I have found is to simply remove the new fonts. But that of course defeats the purpose of having installed the new fonts in the first place.

Here is the procedure I followed to install the new fonts:

```

01. Create a temporary folder in the Home folder. Call it FontsOfLuke.

02. Put the new fonts into this temporary “FontsOfLuke” folder.

03. Create a folder in the Ubuntu system for the “Fonts Of Luke” fonts to reside.

sudo mkdir -p /usr/share/fonts/Fonts_Of_Luke

04. Copy the font files from the temporary “FontsOfLuke” folder to the Ubuntu system font folder just created (Fonts_Of_Luke).

sudo mv ~/FontsOfLuke/*.* /usr/share/fonts/Fonts_Of_Luke/

05. Reset the font cache.

sudo fc-cache -f -v

06. Delete the temporary “FontsOfLuke” folder.
```

PS. Isn't there a decent font manager for 16.04?

---

### Post by ian-weisser on 2016-09-30
Does the annoying font share characteristics with the desired font? Name, class, type, family, or other common attribute that would tell the system to substitute one for the other?

Applications don't choose fonts at random, and the system does not provide fonts at random. Both simply follow instructions.

---

### Post by buzzingrobot on 2016-10-01
The fontconfig program, broadly speaking, controls font selection and use, if a program honors it. (I'm not sure how LibreOffice deals with it.)

Fonts, of course, need to be installed before they can be used. If a program wants to use a specific font that is not available, it may use another font as specified by fontconfig. 

Fonts displayed in browsers are determined by the CSS file associated with the page. It's also common for a font to be downloaded during the page load.  Those fonts will be used by the browser  no matter what fonts are permanently installed on a system.

Both fontconfig and CSS files establish "sans", "serif" and "mono" as final fallbacks. These are not fonts,  They are accepted conventions that must be mapped to an actual specific font.  E.g., "Sans" is very often mapped to Dejavu Sans. A program may have a first preference to use a specific sans-style font.  If that is not available, it may try to use another.  Eventually, if will fall back to the font mapped to "sans".

In other words, if you tell a program to use "Sans", it will generally try to use the first font in the chain of fonts mapped to Sans, falling through to "Sans" when needed..  If you tell it to use, say, "Arial", it will *generally* use Arial if it's installed.  If Arial is not installed and if fontconfig has mapped Arial to, say, Liberation Sans, then Liberation Sans will be used. 

So, it's possible to install fonts that programs will use without user intervention simply because the programs were previously falling back to other fonts.

---

### Post by lukon on 2016-10-01
> **ian-weisser said:**
> Does the annoying font share characteristics with the desired font? Name, class, type, family, or other common attribute that would tell the system to substitute one for the other?

I do not know. How can I check for such similarities or "shared characteristics"?

The problem is now fixed.

The problem was caused by just one of my new fonts having been improperly "named" by it's designer. It was this font that got substituted for the one's I really wanted. It was called "Alien League", under the file name "alien5.ttf".

I replaced this "alien5.ttf" with a different set of ttf files for Alien Leage that had been properly "named" and it all works fine now.

This solution comes from a web page dealing with the Alien League font applied to OSX. But I guess it really pertains to all unix-ish OS's. Here is that web page: [https://discussions.apple.com/thread/3312154?tstart=0](https://discussions.apple.com/thread/3312154?tstart=0)

---

### Post by DuckHook on 2016-10-01
You asked for a post to be deleted, which I have done. In future, you can make such requests by using the "report post" button at the bottom of each post. A staff member will then jail (delete) the post for you.

---

