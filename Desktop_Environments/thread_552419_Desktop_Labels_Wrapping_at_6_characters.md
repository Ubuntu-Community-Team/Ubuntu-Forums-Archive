---
title: "Desktop Labels Wrapping at 6 characters???"
date: 2007-09-16
forum: Desktop Environments
---

### Post by fl1pper on 2007-09-16
This being Linux I have faith that a paragraph of arcane command line stuff in the console, aimed at the gconf quagmire will probably be the 'easy' way to resolve. But what are the parameters called for the line-wrapping config for labels?

I have drive icons on the Desktop, like most people, but one of them, "Content" for example, wraps the final 't' to the second line of the label. WTF? Six characters and then a defaulted auto-wrap to a newline?

Whose idea was that?

Setting the Desktop font to a size of '8' shrinks the font, but the lines still wrap at this retarded, arbitrary point. I got to nbe honest, Linux is fun to 'hobby' around on, but it's no wonder OS X is kicking its *** on the desktop, as far as non-MS installations go.

Thanks for any advice or 'rocket science' methods to accomplish YA-Trivial preference change.

Cheers,
Brian Stegner

---

### Post by Happy_Man on 2007-09-16
I don't get that at all. Not even 14 character names split. I use the Sans Serif font at size 10.

---

### Post by Wolki on 2007-09-16
> **fl1pper said:**
> I have drive icons on the Desktop, like most people, but one of them, "Content" for example, wraps the final 't' to the second line of the label. WTF? Six characters and then a defaulted auto-wrap to a newline?

That definitely shouldn't happen - the names wrap at some point, but shouldn't after six letters. It's based on the width of the label and on my computer seems to be after 10 ems.

Do you have narrow icon view enabled in nautilus? It will set the wrap point earlier. (open the file manager, Edit->Preferences, first tab, second hading, first checkbox). Is your dpi setting very unusual? (see the fonts configuration)

---

