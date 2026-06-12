---
title: "Browser fonts change when installing new fonts in Ubuntu"
date: 2009-07-06
forum: Desktop Environments
---

### Post by openxs on 2009-07-06
I have installed some new fonts on my Ubuntu/Gnome laptop, these work fine. However, when I open Firefox, or any other browser, the default fonts seem to have changed. 

For example, when I do a search in Google, the results are displayed using 'Comic Sans' instead of plain Sans. The fonts used in the browsers chrome remain unaffected,  it's just the actual pages that are affected. Some sites are also rendering incorrectly. This makes me think that the pages css, or perhaps the browsers css needs a tweek somewhere.

I tried installing my fonts in different directories to see if this made any difference, I tried the following directories:

/usr/share/fonts
/usr/share/X11/fonts
/usr/local/share/fonts
~/.fonts

I checked the preferences in Firefox and the fonts are still set as the default of Sans, but changing this makes no difference as expected. 

I'm going to try installing Firebug and experiment with the CSS and see if this makes any difference, in the mean time, has anyone else had this problem? Any Suggestions? 

Thx

---

### Post by openxs on 2009-07-06
I Solved my own problem, and it was indeed CSS related, specifically the Arial font. Wherever the CSS on affected pages declared Arial in the Font-Family it displayed comic sans... weird.

I used Firebug to change fonts by over riding the CSS, to make this permanent I made the following changes in Firefox.

Edit >> Preferences >> Content >> Fonts & Colours >> Advanced >> then **Untick** 'Allow pages to choose their own fonts'.

Hope this helps someone else ;)

---

### Post by ikester8 on 2009-07-06
> **openxs said:**
> Hope this helps someone else ;)

Yes, it does, thank you!

---

