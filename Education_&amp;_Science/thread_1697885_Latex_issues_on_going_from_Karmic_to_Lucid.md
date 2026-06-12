---
title: "Latex issues on going from Karmic to Lucid"
date: 2011-03-01
forum: Education &amp; Science
---

### Post by CUJimmy on 2011-03-01
Hi All,

I have found this question in a couple of threads from several months ago (e.g., [http://ubuntuforums.org/showthread.php?t=1482326&highlight=natbib](http://ubuntuforums.org/showthread.php?t=1482326&highlight=natbib)), but I haven't come across a solution that works for me. My thesis, written using latex, built perfectly in Karmic, but now fails to build in Lucid. From scouting around the forums I think the problem is related to natbib. Latex fails to include any references, and puts up an error after processing each figure:

! Extra }, or forgotten \endgroup.
\color@endbox ->\egroup 
                        
l.19 \end{figure}

I grabbed the latest version of natbib, but this didn't solve the problem. Has anyone come across (and solved) this issue?

Thanks, Jim

---

### Post by PGScooter on 2011-03-02
what command are you using? I'm guessing "pdflatex"?
Does it work with the command "latex"?

---

