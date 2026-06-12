---
title: "Please help with Latex Layout!"
date: 2009-05-03
forum: Education &amp; Science
---

### Post by MetapostAddict on 2009-05-03
Hi all,

I'm going crazy trying to set up the proper margins for my honors thesis, and I'd really appreciate any help.

My needs are simple: I need 1 inch margins on top, bottom and right, and 1.5in margins on left.  

I tried geometry package, but when I print it out the dimensions are way off what I set.

I tried manually setting everything, but still the margin are way off.

argh it's driving me crazy! 

below is what I've tried...


> 
\setlength\voffset{-.75in}
\setlength\topmargin{0in}
\setlength\headheight{.125in}
\setlength\headsep{.375in}
\setlength\textheight{9in}
\setlength\footskip{0in}
\setlength\hoffset{0in}
\setlength\oddsidemargin{.5in}
\setlength\textwidth{6in}


> \usepackage[truedimen,paperheight=11in,paperwidth=8.5in,hdivide={1.5in,6in,1in},vdivide={1in,9in,1in},showframe,dvips]{geometry} 


Thanks in advance for any help

---

### Post by favilac on 2009-05-03
Try this:

\usepackage{geometry}
\geometry{verbose,tmargin=1in,bmargin=1in,lmargin=1.5in,rmargin=1in}

---

### Post by hubie on 2009-05-03
As I understand the geometry package, you fill in the values that you want and it autocompletes the rest.  Because of interdependencies on a lot of those parameters, you can get into trouble if you try to set all of them yourself.

The [documentation]("http://www.tex.ac.uk/tex-archive/macros/latex/contrib/geometry/geometry.pdf") for the geometry package states that if you want to use hdivide and vdivide, you should not specifiy all three values.  You should specify two and leave the other to be calculated.

Try something like
```
\usepackage[letterpaper,left=1.5in,top=1.0in,bottom=1.0in,right=1.0in]{geometry}
```

I think you can even shorten this up with 
```
\usepackage[letterpaper,margin=1in,left=1.5in]{geometry}
```
I can't check these because I can't get on to my latex machine right now.

---

### Post by MetapostAddict on 2009-05-04
I finally figured out the prolem(s), using [http://www.ctan.org/tex-archive/macros/latex/contrib/IEEEtran/testflow/](http://www.ctan.org/tex-archive/macros/latex/contrib/IEEEtran/testflow/)

that site has a LaTeX diagnostic procedure, which helped me discover that dvi defaults to a4 paper size, even if you specify in LaTeX that you're using letter.

If anyone else needs to take their margins seriously, the above link is extremely helpful.

---

