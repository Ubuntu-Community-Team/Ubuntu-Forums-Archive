---
title: "Automatic line breaks in Chinese text in XeTeX?"
date: 2009-03-21
forum: General Help
---

### Post by orchidfire on 2009-03-21
Hi all,

I switched over to XeTeX after having difficulty inputting in Japanese and Chinese in LaTeX.  So far, it's working perfectly, except for one thing:  If I have a long line of Chinese text, which happens when I'm doing homework or writing an essay, I will have to manually break the lines so that it fits correctly on the page.  At the moment, this is just a minor annoyance, since my work doesn't happen to be very long.  However, I foresee this becoming a major problem later on, when my texts become longer.

Is there a package or fix for this?  Some way to specify width or something I can add for automatic line breaks?

Thanks in advance!

---

### Post by jeteve on 2010-11-05
I've got exactly the same problem,

If it can be of any help, using the french polyglossia main language fixes the problem, but at the cost of having your document strings in french ...

Did you reach a better solution?

---

### Post by jeteve on 2010-11-05
Ok, I found the proper solution.

Look at this document: [http://www.tug.org/texmf-dist/doc/xetex/base/XeTeX-notes.pdf](http://www.tug.org/texmf-dist/doc/xetex/base/XeTeX-notes.pdf) , go to section 5.6: Line breaking without spaces

You can use \XeTeXlinebreaklocale"zh" (somewhere in your preamble)

---

