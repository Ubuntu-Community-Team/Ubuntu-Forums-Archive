---
title: "How do I get Indic fonts to work ?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by aneeshm on 2006-07-18
What do I need to do to get Indic fonts ( esp. Devanagari ) to display correctly in Firefox ?

---

### Post by aneeshm on 2006-07-19
*BUMP*

Any help here ?

---

### Post by aneeshm on 2006-07-19
I'll post a screenshot of the problem .

---

### Post by petersjm on 2006-07-19
I'd have thought if a website uses Devanagari and you have it installed on your system, shouldn't it function correctly anyway? Unless you mean you want to use Devanagari on your own website and make others see it - which they won't unless they have the font file themselves...

---

### Post by aneeshm on 2006-07-19
> **petersjm said:**
> I'd have thought if a website uses Devanagari and you have it installed on your system, shouldn't it function correctly anyway? Unless you mean you want to use Devanagari on your own website and make others see it - which they won't unless they have the font file themselves...
I have ttf-indic-fonts installed , which includes devanagari fonts . Even then , the problem that I have shown in the attached photo remains on my computer . That's the whole problem - I have devanagari installed on my system , but it doesn't function correctly ( as shown in the photo ) .

---

### Post by joneall on 2007-01-11
Where did you get this test of Devanagari font installation?  I'm sure I have the same problem, with the matras inverted relative to the characters.

Any answer yet?

---

### Post by rohan000 on 2007-08-12
I have the same problem - it works fine in all other Ubuntu applications but not in Firefox.

---

### Post by rohan000 on 2007-08-18
Start Firefox with the following command:

MOZ_DISABLE_PANGO=0 firefox

If it works, then you can make it permanent by adding the line

MOZ_DISABLE_PANGO=0

to the file /usr/bin/firefox

---

### Post by srinivaschavan on 2007-09-11
Having same problem with ubuntu feisty amd64 with firefox 2.0.0.6.
MOZ_DISABLE_PANGO=0 firefox  --- did not work for me :(

---

### Post by dushkal on 2007-09-13
Hi,

I had the same problem, but I could solve it by installing the correct language packs and locales (as I saw in the FF script that the fonts are displayed correctly only if the locale is installed on the script)

so, try installing marathi locale and marathi language pack, I don;t have the correct package names now, but I'm sure you can find it...

If not, please let it be known here, so that we can compare the configurations. I can see the wikipedia pages correctly..without setting PANGO

---

### Post by s26c.sayan on 2007-09-13
In Firefox, try setting the default encoding type to UTF-8 or some unicode coding!

Also, I agree with the previous poster that you shld install the relevant locale and language packs from the 'Language' in the ubuntu menus.

---

### Post by fiero_ka on 2007-10-26
[http://varamozhi.wikia.com/wiki/Help:Contents/Unicode:_How_To](http://varamozhi.wikia.com/wiki/Help:Contents/Unicode:_How_To)
[http://en.wikipedia.org/wiki/Wikipedia:Enabling_complex_text_support_for_Indic_scripts](http://en.wikipedia.org/wiki/Wikipedia:Enabling_complex_text_support_for_Indic_scripts)

I found help at these two links. Though, It is still not perfectly alright.

---

