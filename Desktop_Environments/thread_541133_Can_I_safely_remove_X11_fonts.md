---
title: "Can I safely remove X11 fonts?"
date: 2007-09-02
forum: Desktop Environments
---

### Post by stopsatgreen on 2007-09-02
Some of the X11 fonts - Helvetica for example - are unaliased and quite jagged, so when I enter a website with one of those fonts as default, it looks terrible. I'd rather have no Helvetica at all than an unaliased one; can I remove fonts from the X11 folders without any adverse effects? What are X11 fonts needed for?

---

### Post by ddrichardson on 2007-09-03
Firefox gives you the option under tools/options/fonts/advanced to change the fonts for given types. I wouldn't recommend just deleting the fonts as depending on how X applications are writeen it may cause problems.

---

### Post by stopsatgreen on 2007-09-03
Thanks for the reply, although not exactly what I meant. Rather than the default fonts in Firefox, I wanted to know about across all browsers; here's a clearer example:

Say I go to a site where the CSS fonts are listed in this order:

Helvetica, Arial, Sans-Serif;

I don't have Helvetica installed, except for the unaliased X11 version, which displays horribly; rather than put up with the unaliased bitmap version of Helvetica, I want to know if I can uninstall or remove it so that my browser displays Arial instead.

Is it okay to remove the X11 Helvetica? What are X11 fonts used for?

---

### Post by kerry_s on 2007-09-03
i recommend you use a .font.conf file instead. you can have it substitute another font in place of helevicta.

i just have my browser set up not to use the site fonts, but my fonts instead.

---

### Post by mrv on 2007-10-09
What I'd think is happening that for some reason you have bitmap fonts enabled. I had on my desktop computer.

Look at /etc/fonts/conf.d directory, and delete any "70-yes-bitmaps.conf" file there might be there. There _should_ be the no-bitmaps.conf as usual.

If someone else knows a better way to handle these issues, please tell. I used to have ugly fonts in eg. Yelp when using bitmap fonts (like Helvetica from xfonts-75dpi/xfonts-100dpi), but removing that file fixed that.

---

### Post by kerry_s on 2007-10-09
> **mrv said:**
> What I'd think is happening that for some reason you have bitmap fonts enabled. I had on my desktop computer.

Look at /etc/fonts/conf.d directory, and delete any "70-yes-bitmaps.conf" file there might be there. There _should_ be the no-bitmaps.conf as usual.

If someone else knows a better way to handle these issues, please tell. I used to have ugly fonts in eg. Yelp when using bitmap fonts (like Helvetica from xfonts-75dpi/xfonts-100dpi), but removing that file fixed that.

**sudo dpkg-reconfigure fontconfig-config**

---

