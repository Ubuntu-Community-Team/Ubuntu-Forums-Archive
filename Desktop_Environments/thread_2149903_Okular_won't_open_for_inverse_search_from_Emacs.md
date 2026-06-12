---
title: "Okular won't open for inverse search from Emacs"
date: 2013-05-30
forum: Desktop Environments
---

### Post by jazzgossen on 2013-05-30
Lately, Okular won't open when trying to view a latex document from Emacs (using AucTex)

The command line sent by the View command is 
```
okular --unique status.pdf#src:1`pwd`/./status.tex
```

If I run the same command line in a terminal I get the error message:
"Error: Can't open more than one document with the --unique switch"

It has been working until a couple of days ago, and I haven't changed any settings in Emacs or Okular. I suspect there might have been an update that broke something, but I can't tell which one.

Shouldn't this command line work? Is there another way to do it? Did something change in Okular's command-line parsing recently?

I'm running Kubuntu 13.04 with Okular 0.16.2, KDE platform 4.10.2, Qt 4.8.4.

---

### Post by jazzgossen on 2013-05-30
Ah.... I solved it.

The problem was that my current document was in a path that had a space in it. I renamed the "spaced" directory, and now everything is as before.

Annoying, though, that it doesn't work with spaces.

---

### Post by jazzgossen on 2013-05-30
Actually, I didn't quite solve it. Although Okular starts now, forward and inverse search no longer works...

For the record, there are two ways I can make Okular start from emacs when the path contains spaces: either remove the spaces (duh) or enclose the argument in citation marks, like so:
```
'(TeX-view-program-list (quote (("Okular" "okular --unique %o#src:%n\"`pwd`/./%b\""))))
```

---

### Post by SeijiSensei on 2013-05-30
Remember that the space is the default delimiter in the bash shell, so anything with a space in it will be split apart.  As you discovered the solution to this is to put the string inside quotation marks.  If you use single quotes ('), the string will be interpreted literally; double quotes (") enable you to enclose environment variables in the string.  For instance,

```

EXAMPLE='this is an example'
echo '$EXAMPLE'
echo "$EXAMPLE"

```

The first returns the literal string "$EXAMPLE" while the latter replaces the environment variable with its contents and returns "this is an example".

---

### Post by jazzgossen on 2013-05-30
I don't know what happened, but forward and inverse search do work. So it was just a thing with the spaces, then. Problem solved. 

And thanks for your input, SeijiSensei.

---

