---
title: "Problem installing .sty for LaTeX"
date: 2005-12-13
forum: Desktop Environments
---

### Post by _kresten on 2005-12-13
Hi!
I'm currently writing my bachelor assignment in philosophy. I'm  writing about logic so it seemed natural to use LaTex. I use the default (synaptic) installation (with emacs21). 
   I've found a .sty-file that seems to enable me to write a speceial notation that the german logician Frege used. But I don't know how to install it... :confused: 
Does any of you guys know how it's done (or do you know somebody that does)? 
I would greatly appreciate any help! 

Go easy on me by the way. I'm still a bit new both to Linux and LaTeX ;)

---

### Post by hod139 on 2005-12-13
The easiest way to use a latex .sty file, is to simply put it in the same directory containing the .tex file.  This of course means you have to put a copy of the style file into every project you want to use it on.  If you want to install it globally, so all future projects can use it, just post back here asking and I can walk you through that as well.

What style file is it?  It might be in the tetex-extra package (which imho should be installed with the tetex-base package).  In any case, if you are going to be using latex, I suggest installing the tetex-extra package as well, since it contains many useful styles (like amstex).
```
 sudo apt-get install tetex-extra 
```

---

### Post by _kresten on 2005-12-14
> The easiest way to use a latex .sty file, is to simply put it in the same directory containing the .tex file.  
Tried that, but no luck... Should I add anything in the beginning of my .tex-file?
>  What style file is it?  
Attached below (just unzip)

By the way: Thanks for helping!

---

### Post by _kresten on 2005-12-14
Heureka!
I added the line
```
\usepackage{begriff}            %Frege notation
```
In the first part of my .tex file and then it worked!

If you have the time I would love to get a howto pointed out for me...:D 

Thanks for helping!

---

### Post by fdimmling on 2005-12-14
To make a style file available systemwide you have to copy it to the TeX tree, e.g by

sudo cp xyz.sty /usr/share/texmf/tex/latex/tools
sudo texhash

For the first line to work you have to be in the directory where your style file xyz.sty is located. The second line refreshes the TeX file database, otherwise TeX or LaTeX will not find the style.

Friedrich

---

### Post by _kresten on 2005-12-14
Vielen dank! ;) 
Will try it out later... For now I'm sticking to the solution where it's just available for the one document.

---

### Post by hod139 on 2005-12-14
I'm glad you got the style file working.  I guess I didn't realize that you wanted help with LaTeX commands.  A decent online latex tutorial can be found at: [http://www.tug.org.in/tutorials.html](http://www.tug.org.in/tutorials.html)
LaTeX can be confusing to learn at first, but once you know the commands there is nothing better for writing technical papers.  I'm glad to hear someone outside of computer science or math is using it.  This could make for an interesting poll, maybe I'll start one.

---

### Post by fdimmling on 2005-12-14
[QUOTE=hod139] I'm glad to hear someone outside of computer science or math is using it.  This could make for an interesting poll, maybe I'll start one.[/QUOTE]

I'm using LaTeX mostly for articles and a  book on Chinese medicine where I need a lot of Chinese characters in both text and index, bibliography. There is nothing that could compete with LaTeX and Emacs with auctex and reftex to generate crossreferences and citations.

Friedrich:cool:

---

### Post by _kresten on 2005-12-21
>  I'm glad to hear someone outside of computer science or math is using it.
Well... I'm not completely outside computer science. That is actually my second major (at my university we choose two majors). But I know that a lot of those writing about philosophical logic do tend to use LaTeX, simpely because there's no alternative.

---

