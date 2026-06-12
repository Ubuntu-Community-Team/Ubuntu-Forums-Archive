---
title: "How faithful is Character Map?"
date: 2009-04-06
forum: General Help
---

### Post by John Jason Jordan on 2009-04-06
I never had any reason to question this before, but I have been having odd results with any of several fonts - Junicode and FreeSerif to mention just a couple. When I enter IPA characters such as the following:

[b&#618;t&#865;&#643;]

It appears fine in Scribus, OOo, Abiword and KWord, until I apply bold. That is, regular and italic work fine, but with bold and bold-italic the IPA characters drop out.

I normally use OOo, but because of this (and other bugs in OOo 3.0.1 on Intrepid), I have been playing with LyX. Using XeTeX so that I can use installed fonts I am finding the exact same behavior. Yet TeX-LaTeX-LyX use their own engine to render to PDF. 

When I look at the above fonts in Character Map they do display the Bold and Bold-Italic IPA characters, and they're the real characters as designed by the font artist, not some generic placeholder character.

I need to be positive that the characters do exist in the font. Can I trust Character Map? Is there another tool that will tell me what glyphs the font has?

---

### Post by cariboo on 2009-04-06
I can't answer your question, but I have asked the mods to move your post to General Help, so that more people will see it. This is not a 64-bit only problem.

Jim

---

### Post by bapoumba on 2009-04-06
> **cariboo907 said:**
> I can't answer your question, but I have asked the mods to move your post to General Help, so that more people will see it. This is not a 64-bit only problem.

Jim
So mooved, thanks cariboo ;)

---

### Post by John Jason Jordan on 2009-04-06
Thanks for moving the post.

However, I have sort of resolved the issue. That is, I now know the font I was using does not have the glyphs I was trying to use. I used Fontforge to open the font files. So, for me, the issue is resolved.

The font in question is Junicode (it's in Synaptic, if you're interested). The majority of the glyphs in the IPA extensions section are not available in bold or bold-italic. But if you look at this section of the font in Character Map, then click on Bold and/or Italic, the characters remain the same.

So Character Map needs spanking. It's a bald faced liar. It displayed all the glyphs, exactly as they should appear considering the design of the font. This cost me a lot of work trying to troubleshoot the issue.

---

