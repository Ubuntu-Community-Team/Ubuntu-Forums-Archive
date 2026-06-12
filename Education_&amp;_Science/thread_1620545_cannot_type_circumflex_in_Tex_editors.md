---
title: "cannot type circumflex in Tex editors"
date: 2010-11-13
forum: Education &amp; Science
---

### Post by Toxicbits on 2010-11-13
Hi,

I have the problem that in editors like Texmaker or TeXworks i can't enter the circumflex by pressing it twice. Pressing it once and then a number makes it be in superscript, but thats of no use for Latex. I guess it is related to the encoding. I use  \usepackage[latin1,utf8]{inputenc} and the file is encoded as utf8.


Some time ago i worked on the same file and I didnt have any problems. Does anyone know how to fix this, cause its really annoying


Thanks toxicbits

---

### Post by Chronon on 2010-11-13
Maybe this helps:
[http://en.wikibooks.org/wiki/LaTeX/Accents](http://en.wikibooks.org/wiki/LaTeX/Accents)

---

### Post by Toxicbits on 2010-11-13
Thats not the issue. I can type &#8312; or ê but not ^, as I would need it to get Supercript after compiling. Even usingtextcomp it didnt work. Didn't this occur to anyone else?

---

### Post by Chronon on 2010-11-15
How about this:
[http://www.wisdomandwonder.com/link/2000/how-to-render-a-carrot-in-normal-latex-text](http://www.wisdomandwonder.com/link/2000/how-to-render-a-carrot-in-normal-latex-text)

---

### Post by Toxicbits on 2010-11-15
I can't even type ^ in my editor and I don't need it to appear in my PDF, but to get "Welcome to the 21st (thats supercript) century." I had to type "Welcome to the 21$^{st}$ century." which I can't.

---

### Post by favilac on 2010-11-16
Ok, so you type '^' and nothing appears in your editor. Am I understanding correctly?

If that is the problem, it has nothing to do with LaTex. It's a problem of your keyboard layout preferences. For to appear, I have to press de ^ button and then the space button. Also, in your post that character did appear. You didn't have the problem in the web form? Or did you make a a C&P from another place?

This is to rule out a configuration or hardware problem.

---

### Post by Chronon on 2010-11-16
Toxicbits: Your initial threads made it sound like LaTeX was refusing to render that character properly (or combine them with others).  I agree with favilac that this problem has nothing to do with LaTeX and that the most likely culprit is some localization setting somewhere.

Is it impossible to type this character system-wide for you?

---

### Post by Toxicbits on 2010-11-16
I can type ^ systemwide, except for editors like Texmaker or Texlive. If I edit the same file in gedit it works fine.

---

### Post by Chronon on 2010-11-16
I have never used those programs so I can't help specifically with configuration of those.  I always used geany to edit my LaTeX files when I used Gnome.

Edit: Is this possibly a problem with SCIM?  I found this post which might possibly have something to do with what you're seeing: [http://ubuntuforums.org/showpost.php?p=7029209&postcount=59](http://ubuntuforums.org/showpost.php?p=7029209&postcount=59)

---

