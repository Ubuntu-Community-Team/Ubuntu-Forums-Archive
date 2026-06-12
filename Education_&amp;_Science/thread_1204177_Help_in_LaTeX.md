---
title: "Help in LaTeX"
date: 2009-07-04
forum: Education &amp; Science
---

### Post by 7raTEYdCql on 2009-07-04
I need some help in LaTeX. Here are some of the problems that i am facing.

1. I want to draw two tables side by side, but my document is not set in twocolumn format. Is there anyway i can set a certain section of my page in twocolumn format, so that i can draw the two tables.

2. I want to draw a flowchart in my document. Can someone introduce me to this, i haven't found any good tutorials on the net. 

3. Is there a way in which i can draw Electrical Circuits in \LaTeX.

4. I want to draw arrows to indicate certain points on my images, can this be done in \LaTeX directly, or should i do it in Paint or something and then directly \includegraphics{theimage}.

Just in case it is needed, i am using Ubuntu, with the \LaTeX plugin for gedit.

---

### Post by myle on 2009-07-04
[LIST=1]
[*][http://texblog.wordpress.com/2007/08/01/placing-figurestables-side-by-side-minipage/](http://texblog.wordpress.com/2007/08/01/placing-figurestables-side-by-side-minipage/)

[/LIST]

2 - 3: May google be with you
4: I think yes, but I can't recall where I had found the package which did what you are asking.

---

### Post by xadder on 2009-07-04
For 4 I think pstricks does the job. On the other hand, xfig, inkscape, or your favourite drawing app may be easier, followed by includegraphics as you suggest. I think pstricks does circuit diagrams though - see the wikipedia entry.

---

### Post by meborc on 2009-07-05
1. you could use \begin{columns} to insert 2 columns in any part of your text

4. check this - [http://www.texample.net/tikz/examples/beamer-arrows/](http://www.texample.net/tikz/examples/beamer-arrows/) maybe this for your arrows?

---

### Post by metricspace on 2009-07-05
you can refer LaTeX forum.
 
[www.latex-community.org]("http://www.latex-community.org")
 
Regards,
metric

---

### Post by hugmenot on 2009-07-05
1. Either you put two boxes side-by-side like two parboxes or two minpages, or you use the multicol package, which gives you multiple columns in an environment
2. I would use TikZ for this: [Example]("http://www.texample.net/tikz/examples/simple-flow-chart/")
3. Also TikZ using [this package]("http://tug.ctan.org/pkg/circuitikz")
4. Use a Tikz image overlay: [Example]("http://www.texample.net/tikz/examples/connecting-text-and-graphics/")

TikZ does similar things like PSTricks, but it is more modern and more comfortable to use. And its documentation is excellent.

---

### Post by 7raTEYdCql on 2009-07-05
Thanks hugmenot. Tikz has solved my problem.

---

