---
title: "Font problems in Google Chrome"
date: 2010-05-10
forum: Desktop Environments
---

### Post by mikebeecham on 2010-05-10
Hi guys,

I recently updated my Lucid setup and now find that the web content fonts in Chrome now look like they have no smoothing. 

Is this a known issue, or is there anything I can try to remedy?  I should mention that the fonts on the Chrome bookmark bar, controls, etc are all fine...it's just on all websites.

Thanks.

---

### Post by Zorael on 2010-05-10
Getting Chrome to display the fonts you want it to isn't easy. >.< I've been trying to get Chromium to display Japanese characters without antialiasing with zero luck so far. It ostensibly sticks to its own rules, so if anything I'm curious as to how you got it to do any different.

Make sure you have sane font choices. Pop up Options and pick the Under the Hood tab, then scroll down to Change the default font and language for webpages. Notably don't pick Sans, Sans-serif or Monospace while troubleshooting; stick to a "real" font. Like Times New Roman or the DejaVu series or whatnot.

Also try renaming your **~/.fonts.conf** to something else and then restart Chrome. Chromium doesn't listen to fontconfig settings much, but some settings (like what font order makes up those Sans, Sans-serif and Monospace virtual fonts) may still matter.

---

### Post by mikebeecham on 2010-05-12
Hi Zorael,

I managed to sort the issue out.  For some reason upgrading to Lucid changed my .fonts.conf file.  I had originally used a custom fonts.conf to turn on autoaliasing.

Lucid seemed to have changed it.  I reverted the conf file back to what it should have been, logged out and back in again.

Hey presto!  It worked and my fonts are tasty again!

Incidentally, I use Myriad Pro fonts because everything is sexy about them in Ubuntu :D

---

