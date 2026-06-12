---
title: "LateX and MLA Style"
date: 2007-12-13
forum: Education &amp; Science
---

### Post by Trash_Gordon on 2007-12-13
Hi,
I am currently writing a term-paper which is due the end of next week. Since we have to use MLA-Style, I was thinking about using LateX. However, I can't find a way to use proper MLA Style. Using the \usepackage{mla} command, I get a fairly good output, but the title still looks like this:

[[IMG]http://img221.imageshack.us/img221/3339/screenshot2wj2.png[/IMG]](http://imageshack.us)

which doesn't look like MLA at all.
Is there a way to get proper MLA format there? I tried to compile MiKTeX from source, as suggested in this board, but it doesn't compile correctly.

---

### Post by Trash_Gordon on 2007-12-13
OK found it. The description is in the /usr/share/texmf-texlive/tex/latex/mla-paper/mla.sty file:

> %    For use with LaTeX and pdflatex.
%
%   To use, 
%   1. Put  \usepackage{mla}  in the preamble
%   2. After the \begin{document}, put \begin{mla}{Firstname}{Lastname}{Prof's lastname}{class name}{date}{Paper title}
%   3. Immediately - the next line - start typing your paper.
%   4. Put   \end{mla}   just before \end{document}
%
%   To use the bibliography feature,
%   1. Use  \begin{workscited} to start the bibliography.  There is no need to 
%      declare a new page or even type "Works Cited" at the top of the page.
%   2. Use   \bibent  before each entry.
%   3. Put   \end{workscited} at the end.


---

### Post by jackthomas2613 on 2012-11-04
I know this may seem like a late reply, but I think it would help people who are still seeking a good answer to this question. I found this package online called MLA13 that does everything for you. I used it in quite a few of my papers already. The thing that's good about it is that it uses your .bib files and formats everything according to MLA standards.

The website for this is:

Documentation: [http://jackson13.info/mla13/Documentation.pdf](http://jackson13.info/mla13/Documentation.pdf)

Download the Sty File: [http://jackson13.info/mla13/mla13.sty](http://jackson13.info/mla13/mla13.sty)

Github: [https://github.com/jackson13info/mla13](https://github.com/jackson13info/mla13)

---

### Post by overdrank on 2012-11-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

