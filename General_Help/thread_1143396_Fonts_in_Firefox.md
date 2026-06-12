---
title: "Fonts in Firefox"
date: 2009-04-29
forum: General Help
---

### Post by lbelloq on 2009-04-29
Gentlemen:

I have a question about a weird Firefox behavior I'd like to correct.
First, please take a look at Exhibit 1: the attachment called *ubuntuforums en firefox win.jpg*. This is haw Firefox renders this page in Windows.
Now, please take a look at Exhibit 2: the attachment called *ubuntuforums en firefox lin.jpg*. This is how Firefox renders this page in Linux.
The problem is, when I recently installed Jaunty, both Firefoxes **rendered the same page in the same way**! I do remember adding some True and OpenType fonts to my .fonts/ folder, but does that have any relationship to this problem?
Any help will be rewarded with free internets.

Thanks in advance,
Léster

---

### Post by mb_webguy on 2009-04-29
Wow.  Big pics.  It's really hard to tell what's going on when each screenshot fills up the entire screen.

Just a guess, but...  The default fonts in Windows and Linux are a bit different.  Linux by default doesn't have Times New Roman (the default Windows serif font) or Arial (the default Windows sans-serif font), so if you don't have those fonts installed, web pages will look a bit different.  Installing the msttcorefonts package will provide these fonts and make pages look more similar.

---

### Post by lbelloq on 2009-04-29
Wait... it was that easy? Wow, I kinda feel ashamed.
Thanks a lot, it worked like a charm.
And as promised, one free internet for your help.

---

