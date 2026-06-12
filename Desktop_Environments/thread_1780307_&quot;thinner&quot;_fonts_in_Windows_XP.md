---
title: "&quot;thinner&quot; fonts in Windows XP"
date: 2011-06-11
forum: Desktop Environments
---

### Post by ieee488 on 2011-06-11
I am dualbooting between Ubuntu 11.04 and Windows XP.

I use Firefox 4 in both OS.

I mainly use Ubuntu, but I must say that I prefer the fonts used in Windows XP's Firefox 4. The fonts "thinner".

Is there a way to achieve this in Ubuntu?

---

### Post by tgalati4 on 2011-06-11
Open a terminal:


tgalati4@tpad-Gloria7 ~/Desktop $ apt-cache search ttf core
ttf-dejavu - Metapackage to pull in ttf-dejavu-core and ttf-dejavu-extra
ttf-dejavu-core - Vera font family derivate with additional characters
ttf-indic-fonts-core - Core collection of free Indian language fonts
ttf-unfonts-core - Un series Korean TrueType fonts
ttf-aenigma - 465 free TrueType fonts by Brian Kent
msttcorefonts - transitional dummy package
ttf-mscorefonts-installer - Installer for Microsoft TrueType core fonts

sudo apt-get install msttcorefonts

Reboot (that's to give the true Windows feel.)

---

### Post by conradin on 2011-06-11
[http://support.mozilla.com/en-US/kb/Changing%20fonts%20and%20colors](http://support.mozilla.com/en-US/kb/Changing%20fonts%20and%20colors)

alternatively, you could explore the about:config address

---

### Post by ieee488 on 2011-06-11
I should clarify that I was posting about fonts/lettering of Firefox itself. In other words, the fonts used for the menu - File / Edit / View etc, and also I like the icons in Windows XP's Firefox 4 better.

---

### Post by tgalati4 on 2011-06-12
I'm guessing that Firefox itself is not using MS true type fonts.  Otherwise it makes distribution difficult because of the true type font licensing issues.  But the Windows version has the true type fonts available (on the Windows box) so it uses them.

I use chrome and the fonts look OK.

---

### Post by ieee488 on 2011-06-12
I did download the Microsoft fonts, but it turned out I didn't need them.
I changed System -> Preferences -> Appearances -> Fonts -> Application Font from Ubuntu to Ubuntu Light, and it made the fonts more like those in Windows XP. However, the icons still don't look as nice.

---

### Post by ivanovnegro on 2011-06-12
The icons problem is another thing as you are using the version for Ubuntu and not for Windows.
The fonts, wow, XP e.g. has no antialiasing and thats the reason why the fonts looks thinner, I personally dont like this outdated look but maybe some people prefer it.
Ubuntu has antialiasing enabled by default and also hinting set to slight. If you want the XP experience, disable antialiasing and set the font hinting style to full. You can achieve this from the system settings, appearance, fonts.

---

