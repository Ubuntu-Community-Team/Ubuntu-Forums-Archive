---
title: "Why can't my applications don't see newly installed ms fonts?"
date: 2011-10-06
forum: Desktop Environments
---

### Post by lrPrentice on 2011-10-06
Hello,

I need to update some Scribus files. But when I open them, Scribus tells me that they contain fonts that are not installed, including Time New Roman Regualr, Trebuchet MS Bold, etc. I then did a web search, discovered that I need to install ttf-mscorefonts-installer. Which I did. 

But, when I went back to Scribus, it still complained about the missing fonts.

I checked Libre Office. It wasn't seeing the new fonts either.

I double checked the install:

$ sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

I logged out and rebooted the system.

But my applications still don't see the fonts.

Can some kind soul tell me what I am missing?

And why is this so hard?

Many thanks,

LRP

---

### Post by mcduck on 2011-10-06
Maybe some of the fonts your document uses aren't included in the freely distributable Microsoft fonts package. Times New Roman should be, but I'm not so sure about Trebuchet, for example...

In that case you'll have to obtain those fonts through other means and install them manually, either into ~/.fonts or to /usr/share/fonts. Or just let Scribus and LibreOffice substitute those fonts with ones you actually have.

Edit: did you  confirm the EULA when installing the fonts package? I'm just asking because some people have had troubles figuring out how to do that, and simply closing the window without confirmation would leave you with the font installer package installed, but it would never actually download & install the fonts for you...

Edit2: and why is it so hard? Because of the licensing Microsoft used for those fonts, which makes it impossible to include the fonts by default or to repackage them into more easily usable format. Actually they even stopped the whole web fonts project in 2002, and the only reason we can have the fonts at all is that the original licence allowed redistributing them as long as they aren't modified or repackaged in any way.

---

### Post by lrPrentice on 2011-10-06
Thanks McDuck.

I'm pretty sure I check the EULA. But I'll double-check.

I created the Scribus files under Debian Lenny - had no problem.

Clearly more research is in order.

All the best,

LRP

---

