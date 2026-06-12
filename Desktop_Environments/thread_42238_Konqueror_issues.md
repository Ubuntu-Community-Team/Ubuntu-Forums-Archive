---
title: "Konqueror issues"
date: 2005-06-16
forum: Desktop Environments
---

### Post by jhk on 2005-06-16
I've been messing around with Konqueror recently, and I like it's speed and the amount of controls it has, but I have a few niggles about it.

I've set Bitstream Vera fonts to use, but whenever a page specifies a font name konqueror will not use a Bitstrean font but instead whatever it seems to think matches, with the result that some crappy fonts are used and text doesn't look good.  In Firefox, I can click 'always use my fonts' to force Bitstream fonts, but the only way to do that in konqueror seems to use the 'customize' tab under CSS in 'configure konqueror,' and force it to use Vera Sans.  But then it also disables all backgrounds, even if the check box that does that is turned off!  That makes most webpages look funny because all you see is basically black font on white.

Also, the foward and back buttons for web browsing on my mouse don't work in Konqueror, even though I've set everything up fine using imwheel based on stuff I've read here and they work in other applications.

I've attatched an image (I think) of an example of the crappy fonts I mentioned.  Look at the k and v on line 4 of the center paragraph.  It looks a lot better using Bitstream Vera fonts.

Thanks for the help!

-JHK

---

### Post by philipacamaniac on 2005-06-17
That "K and V" issue is with the Verdana and Tahoma fonts. I noticed it on my machine, but never reported it. It's like the font smoother doesn't know how to smooth certain characters in MS TrueType fonts.

If you remove Verdana and Tahoma, Konqueror will probably fall back to Bitstream Vera Sans on most websites.

Perhaps this is a bug (if only a small one)?

---

### Post by jhk on 2005-06-17
Yeah, removing Verdana (I don't seem to have Tahoma installed) fixed the font issue.  Thanks!

Now, does anyone know how to make Konqueror 'see' my mouse's foward and back buttons like all my other applications?  :)

---

