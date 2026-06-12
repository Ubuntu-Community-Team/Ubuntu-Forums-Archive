---
title: "Latex and Thesis Class Files"
date: 2008-01-29
forum: Education &amp; Science
---

### Post by Callandor4 on 2008-01-29
I am trying to use latex to begin writing my thesis, and have run into a maddening problem.  My university provides a class file, cornell.cls, that I have moved to the texmf-texlive/tex/latex/base directory.  I began editing the sampleThesis.tex document that was also with the cornell thesis files, and additionally added the packages that were being used by this file to the proper directory (except hangcaption, I can't find it.)  Everything compiles fine until I begin to add text to my abstract section.  After I do this, when I compile I get two errors over and over, "extra \else" and missing \endcsname.

I am going crazy.  I can provide anyone who can help with whatever information they need.  I am using Kile, but it seems I have the same problem using texmaker.  Thanks!

-Kyle

---

### Post by GSBoomer on 2008-01-31
Kyle,

I've been watching your post for a few days hoping someone (else) would help. I don't know much about LaTeX, but I did write my dissertation using custom class files at Florida State.

When I ran into snags, which I did frequently, there was a LaTeX guru on campus who helped tremendously. She even helped me get the class files set up to use on LyX.

If I were you, I'd examine the cornell.cls file and figure out who wrote the damn thing and ask them for help. I bet they want to make sure the class files are as easy to use as possible.

(Hey, a thought ... you did run texhash after installing the new files, yes?)

Good luck.

---

### Post by euler_fan on 2008-01-31
> **Callandor4 said:**
> I am trying to use latex to begin writing my thesis, and have run into a maddening problem.  My university provides a class file, cornell.cls, that I have moved to the texmf-texlive/tex/latex/base directory.  I began editing the sampleThesis.tex document that was also with the cornell thesis files, and additionally added the packages that were being used by this file to the proper directory (except hangcaption, I can't find it.)  Everything compiles fine until I begin to add text to my abstract section.  After I do this, when I compile I get two errors over and over, "extra \else" and missing \endcsname.

I am going crazy.  I can provide anyone who can help with whatever information they need.  I am using Kile, but it seems I have the same problem using texmaker.  Thanks!

-Kyle

First, TeTeX is a fine *basic* distribution, but it really isn't much maintained anymore nor comprehensive. I would uninstall it and get TeXLive (also in the repos) instead. It may have most of what you need already and preconfigured.

[Here's a tutorial on adding new LaTeX style files to your distribution.]("http://blog.irrepupavel.com/2007/02/installing-latex-style-files-sty-on.html") I like it greatly and hve used it myself on several occasions.[This is a link about one of your error messages.]("http://web.mit.edu/answers/latex/thesis/latex_thesis_contents.html") From MIT admittedly, but quite specific. I tried a quick google search on the other one but nothing popped out at me as relevant.

Good luck.

---

### Post by cu_grad on 2008-06-14
While probably too late for Kyle, hopefully this helps others. I had a similar problem that appeared to be a result of \textit{} in the title ({\it } also caused the same problem). I'm not a latex guru, so have no idea why except it have to do with the formatting forced on the title.

---

