---
title: "lyx two columns"
date: 2007-12-22
forum: Education &amp; Science
---

### Post by ragwing on 2007-12-22
I have been trying to make multicols by using ERT \begin{multicols}{2} but I keep getting this error when I try to view it with DVI
LaTex Error: \begin{document} ended by \end{multicols}.

If I click on the error it says:
\begin{multicols}
                     {2}
Your command was ignored
Type | <command><return> to replace it with another command. or <return> to continue without it.

I think this should work, what am I doing incorrect!

Thanks
Rex

---

### Post by kleeman on 2007-12-22
Did you insert

\usepackage{multicol}

in the document preamble i.e. 

Document----> Settings---->Latex Preamble

Works for me with a very simple example....

---

### Post by ragwing on 2008-01-02
Thanks that worked. :popcorn:

---

