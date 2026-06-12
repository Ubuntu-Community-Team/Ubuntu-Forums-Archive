---
title: "[SOLVED] AbiWord Equation Editor Inserts &amp;quot;i&amp;quot; instead of minus"
date: 2007-02-05
forum: Desktop Environments
---

### Post by Kadin2048 on 2007-02-05
I'm not sure if this is the right forum to ask this, but I'm hoping somebody can help me out.

I'm trying to use AbiWord (the default word processor in Xubuntu) to type a document that involves chemical formulas.

The problem I'm running into is that AbiWord's equation editor (Insert>Equation>From Latex) is inserting "i" (seemingly the character used for imaginary numbers) whenever I try to insert a hyphen for a minus sign.

So, if I type "-2" into the box and hit insert, what AbiWord inserts is "i2". Obviously, this is unhelpful.

I'm going to have to switch back to using MS Word on a PC until I can figure this out, because I have a lot of chemical formulae to type, and many of them are things like:
{{C_2}{H_3}{O_2}}^{-}
where the superscript minus sign is critical and cannot be dropped (and certainly not replaced by an i!).

I'm not sure if this is an AbiWord issue or what, but I'm rather desperate here.

Installing OpenOffice, just in case anyone is planning on suggesting it, is not an option. The machine I'm using is FAR too slow to be tolerable with anything heavier than Xubuntu+AbiWord on it. Also, I'd rather not use emacs+LaTeX or a non-WYSIWYG editor.

---

### Post by bteltlt on 2007-03-04
Hey

I'm also having a lot of problems with this. As AbiWord insert equation will nott do most of the latex commands properly, it's displays other symbols from standard commands (such as i instead of -, § instead of \mp).

I tried installing the Fonts mentioned on several pages, but that hasn't worked either. It may of course be that I did something wrong.

But this shouldn't be too complicated a problem, should it?

Anyone have a clue?

Or did you fix it perhaps Kadin2048?

---

### Post by Kadin2048 on 2007-03-04
Unfortunately, I never found a solution. I ended up doing the thing I started off trying in AbiWord, by just handwriting the equations (so much for the 21st century...). Since then, I've had success using TexShop (which is a combination of a LaTeX-specific text editor, plus LaTeX and pdflatex) on Mac OS X, to do all my my chemistry and math writing. (Though you could do the same thing using pdflatex on any other platform, with a suitable context-sensitive editor, like KDE's Kate.)

At least in its default configuration in Xubuntu, I think that the Equation Editor in AbiWord should be considered broken. An equation editor that inserts random symbols in place of what is typed, is more harmful than useful.

---

### Post by bteltlt on 2007-03-05
Thanks!

I agree, the equation-editor is definitely broken. I'm trying out LyX now, and that too seems to be working superbly! :)

Anyway, thanks for teaming up against AbiWord (which otherwise looks like its a good editor, and I would really like the equation editor to be fixed!!)

---

### Post by BrendanM on 2007-03-08
You might also checkout TeXmacs ([http://www.texmacs.org/](http://www.texmacs.org/)) which is a free, WYSIWYG equation editor. I think it generates TeX equations that could then be inserted into Abiword. Good luck.

---

### Post by jsampaio57 on 2007-06-28
You need to install texcm-ttf in order to have Abiword correctly using the fonts in its math editor. Download the font (look for texcm-ttf.zip in the web).  Unpack the folder into /usr/share/fonts/truetype
Then update the font information cache using: 
$ sudo fc-cache -fr

---

### Post by Jaguar0616 on 2007-07-17
Thanks for the tip, jsampaio, that font was just what I needed to get Abiword's equation editor displaying properly.

In a related tirade . . . WTF!? Who's the idiot who added the equation editor to the plugins package without the needed font?

---

