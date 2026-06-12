---
title: "setting latex equation width"
date: 2011-07-04
forum: Education &amp; Science
---

### Post by yairsuari on 2011-07-04
Hi everyone
i am using open office latex equation editor ooolatex
i want to make the width of the equation identical to the text width in open office.
can anyone think of a way to do it?


my code:

\setcounter{equation}{47}
\begin{equation}
\alpha=5
\end{equation} 

after working a whole day five minutes later its somwhat better by adding 
\setlength{\linewidth}{9in}
\setlength{\textwidth}{11in}
 in the preamble the width is now ok the only problem is that the equation counter dissapeared

thanks alot
yair

---

### Post by yairsuari on 2011-07-18
just in case someone reads it in the future:
what i did is adding blanks to make the equation wider by 
\hspace{220mm} this is also not as wide as my page but its wide enough for me and all the equations come out looking the same.

---

