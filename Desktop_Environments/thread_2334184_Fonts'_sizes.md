---
title: "Fonts' sizes"
date: 2016-08-17
forum: Desktop Environments
---

### Post by RadFel on 2016-08-17
Hi,
I installed Ubuntu 16.04, I have a 13,3" Lenovo Thinkpad E330 with 1366x768 (16:9) resolution.

The problem I'm having is the fact that fonts' sizes are too big everywhere and I can't change them in each place I'd want to. For instance, I wish to change them in Firefox, but I only have 2 fonts to choose from there and the changes don't apply to every website, i.e. on web.whatsapp.com the font is still big even if I make it smaller in settings, the same on JIRA's website, on Skype's, etc.

Not to make a mess in this thread, I'll be happy if someone tells me where to manage Firefox fonts fully.

Regards,
Radek

---

### Post by howefield on 2016-08-17
See if Ctrl + - (as Ctrl plus the minus keys) gives you what you want. Ctrl and + key will revert back.

Not quite clear if your issue is restricted to Firefox though, as you say fonts are big everywhere.

---

### Post by RadFel on 2016-08-17
Resizing Firefox windows manually using the key shortcuts you proposed works fine, but it's not the case. I'd like to be able to manage fonts, no the whole sizes of pages...

---

### Post by ajgreeny on 2016-08-17
In FF you can try using the **View menu ->Zoom ->Zoom text only** but I am also not sure if FF is your only problem; it sounds as if you may need changes to the DPI figure in your system's font rendering settings.  Where you find that depends on the DE you are using and I'm not sure where it is in unity.

---

### Post by RadFel on 2016-08-17
Ok, it turned out there was a setting in FF letting websites choose their own font regardless of what I set up. I'm sorry for this confusion. Case closed.

---

### Post by howefield on 2016-08-17
> **RadFel said:**
> Resizing Firefox windows manually using the key shortcuts you proposed works fine, but it's not the case. I'd like to be able to manage fonts, no the whole sizes of pages...

Sorry, not sure what to suggest then, if I navigate to Forefox  > Edit > Preferences > Content.. there is a multitude of fonts and sizes to choose from, selecting the Advanced options also allows to stop websites from choosing their own fonts.  Checked it out with the Skype website which seems to respond to the changes made.

Edit : our replies have collided :) glad you sussed it.

---

### Post by buzzingrobot on 2016-08-17
Changing the font family will not affect font size.  E.g., a 16pt character is a 16pt character.

A default font size and a minimum font size can be set in Firefox's Preferences. 

Preventing a site from using the fonts it was designed to use may break its layout and design. It's common for sites to download the fonts they require during the initial page load.

It's possible that the DPI is set incorrectly, or is being read incorrectly, on the OP's laptop. It should be 96 DPI.  If it is set higher, characters will be larger.

---

