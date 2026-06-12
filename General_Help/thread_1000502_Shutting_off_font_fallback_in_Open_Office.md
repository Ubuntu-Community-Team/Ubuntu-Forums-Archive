---
title: "Shutting off font fallback in Open Office"
date: 2008-12-03
forum: General Help
---

### Post by Frogbarf on 2008-12-03
I've just finished doing studying some fonts that specifically support the Georgian alphabet in various ways. One of the elements of this study was a spreadsheet with blocks of cells corresponding to various contiguous blocks of Unicode characters. I'd select a specific font for these blocks so I could print out a PDF showing the specific characters in it.

Unfortunately, if a character were not available in a given font, Open Office would grab one from some other font and display that. The only way I could generate correct PDFs was to use FontForge to ascertain the actual character complement in a font, then "white out" the characters that had been intruded from other fonts by OO by setting their text color to "white".

This is, of course, an example of the font fallback mechanism within Unicode; the same thing happens in the character map applet.

I know the system is designed to "be nice": "oh, gee, that character you want isn't in that font so I'll give it to you one from another font, isn't that nice of me?"

But in this case, the failure of OO to do what one asked, namely display whatever is at a given Unicode codepoint in a given font and nothing else, caused me a lot of extra, unnecessary work.

I looked around in the OO preferences and options in the hope that there was a toggle to turn off this behavior, but no such luck.

**My question: Does anyone know a way of telling Open Office NOT to substitute for characters missing from the current font? **

---

