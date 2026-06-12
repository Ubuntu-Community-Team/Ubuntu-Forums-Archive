---
title: "xemacs problem &quot;Can't get fontset resource for Input Method&quot;"
date: 2005-05-12
forum: Desktop Environments
---

### Post by motionsiren on 2005-05-12
**FIXED! - I installed xemacs with no mule support. must be a problem with mule?**

Hey all,

Before I start, let me just say that I'm both a emacs *and* vi person. they're both necessary (: anyway...

I installed xemacs with:
```
sudo apt-get install xemacs21
```

It loads up great, even my lisp scripts work (most other distos required I installed this "sumo" package). However, there is one slight problem, the fonts don't look like the typical xemacs fonts and a bottom window pane titled *Warning* says:

```
(1) (xim-xlib/warning) Can't get fontset resource for Input Method
```

now there are more xemacs related packages, perhaps one of these will fix it?

```

xemacs21-basesupport - Editor and kitchen sink -- compiled elisp support files
xemacs21-basesupport-el - Editor and kitchen sink -- source elisp support files
xemacs21-bin - highly customizable text editor -- support binaries
xemacs21-gnome-mule - highly customizable text editor -- Mule binary
xemacs21-gnome-mule-canna-wnn - highly customizable text editor -- Mule binary c
ompiled with Canna and Wnn
xemacs21-gnome-nomule - highly customizable text editor -- Non-mule binary
xemacs21-mule - highly customizable text editor -- Mule binary
xemacs21-mule-canna-wnn - highly customizable text editor -- Mule binary compile
d with Canna and Wnn
xemacs21-mulesupport - Editor and kitchen sink -- Mule elisp support files
xemacs21-mulesupport-el - Editor and kitchen sink -- source elisp support files
xemacs21-nomule - highly customizable text editor -- Non-mule binary
xemacs21-support - highly customizable text editor -- architecture independent s
upport files
xemacs21-supportel - highly customizable text editor -- non-required library fil
es

```

any suggestions or tips would be appreciated! :) thx.

---

### Post by xy77 on 2005-05-13
Same problem here.

I only found

```
   if (!xic_vars.fontset)
     {
-      stderr_out ("Can't get fontset resource for Input Method\n");
+      xim_warn ("Can't get fontset resource for Input Method\n");
       FRAME_X_XIC (f) = NULL;
       return;
     }

```

on this page: [http://list-archive.xemacs.org/xemacs-patches/199911/msg00077.html](http://list-archive.xemacs.org/xemacs-patches/199911/msg00077.html)

but I couldn't figure out what it meant. I tried to change fonts in Xemacs, but it wouldn't help.

- David (xy77)

---

### Post by karlheg on 2005-06-06
The answer is in:

[http://list-archive.xemacs.org/xemacs-beta/200505/msg00090.html](http://list-archive.xemacs.org/xemacs-beta/200505/msg00090.html) 

What I did is create the file "/etc/xemacs21/site-start.d/00AAsuppress-warning.el" with the contents:

```

(add-to-list 'display-warning-suppressed-classes 'xim-xlib)

```

... and either evaluate it with C-x C-e, to keep using the same session, or simply restart XEmacs.

---

### Post by simao on 2005-10-14
Yes that seem to hide the warning, but, did you try to type a "~" or a "^"? I couldn't, it says something like "symbol unknown" or something. Should I compile xemacs, and not install it by debs?
This started happening when I turn on font hinting with fontconfig.

Thank you

---

### Post by simao on 2005-10-20
I have the same problem, any luck finding a solution?


Thank you

---

### Post by shadwstalkr on 2005-11-11
For me the problem was in the xemacs21-mule package.  You want to install the xemacs21-nomule package and remove the xemacs21-mule and xemacs21-mulesupport packages.  Of course, this only works if you don't need mule.  Good luck.

-alex

---

### Post by motionsiren on 2005-11-30
This also fixed it for me too. I guess I don't need Mule *shrug* ;)

---

### Post by Cosmik Debris on 2006-07-03
Another solution is to set LANG=C before starting xemacs.

Works great for me, even with mule installed

---

### Post by troglodyte on 2007-01-25
Starting xemacs with:

     LANG=C xemacs

works for me as well.

Incidently, I don't completely know what elements of xemacs are nonfunctional when this error is present - most of the time everything seems to work just fine. I have found, however, that when working in an R-based ess session, you can't make a call to X11 to plot anything. When the plot function is called, you get the error:

Error in X11() : could not find any X11 fonts
Check that the Font Path is correct.

Also, this problem seems specific to Ubuntu. It would be great to have it fixed in a future update. :)

---

### Post by alex-v on 2007-08-14
I don't know what part of (k)ubuntu QA process is responsible for this but here is what is happening:
1. Standard X11 fonts are in /usr/share/fonts/X11
2. /etc/X11/xorg.conf sets FontPath to /usr/share/X11/fonts/misc etc
3. scripts like update-font-aliases refer /usr/lib/X11/fonts

So what I did was
1. corrected /etc/X11/xorg.conf 
2. created symlink /usr/lib/X11/fonts -> /usr/share/fonts/X11

That took care of the xemacs error.

---

