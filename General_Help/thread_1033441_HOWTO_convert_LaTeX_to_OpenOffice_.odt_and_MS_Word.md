---
title: "HOWTO convert LaTeX to OpenOffice .odt and MS Word .doc"
date: 2009-01-07
forum: General Help
---

### Post by eudemus on 2009-01-07
I have recently (finally!) had success in converting a LaTeX document into OpenOffice (and thence into MS Word), and thought I'd publicise how I did it, in case this can be of help to others.

This page is the place to start:
[http://www.tug.org/utilities/texconv/textopc.html](http://www.tug.org/utilities/texconv/textopc.html)
This page is also helpful (if rather techie):
[http://www.cse.ohio-state.edu/%7Egurari/TeX4ht/mn.html](http://www.cse.ohio-state.edu/%7Egurari/TeX4ht/mn.html)

Basically, I used tex4ht, which is (as far as I can see) clearly the best way to do the conversion.

However, getting the tex4ht installation set up correctly can be a royal pain, so here's how it worked for me.

Step 1. Install tex4ht from the Ubuntu repositories.
Step 2. Install the upgrade from here:
[http://www.cse.ohio-state.edu/%7Egurari/TeX4ht/mn-upgrade.html](http://www.cse.ohio-state.edu/%7Egurari/TeX4ht/mn-upgrade.html)
This is not a simple procedure. You need to follow every single step exactly, and it takes a little while, especially if you are approaching it in a gingerly and careful way, as I was - not really understanding what I was doing! But the instructions are very clear and accurate, and do work. The conversion to OpenOffice won't work without this upgrade.

There are various other steps that may be necessary depending on what is in your LaTeX file. If, like me, you are using biblatex, you will need to install Eitan Gurari's bug fixes from here:
[http://www.cse.ohio-state.edu/~gurari/TeX4ht/bugfixes.html](http://www.cse.ohio-state.edu/~gurari/TeX4ht/bugfixes.html)
I also needed to (re)install an up-to-date version of csquotes from here:
[http://www.ctan.org/tex-archive/macros/latex/contrib/csquotes/](http://www.ctan.org/tex-archive/macros/latex/contrib/csquotes/)
For some reason, it seemed to be the case that I needed to install dvipng from the repositories (though I don't really understand why).

At that point, things should be ready. Run the following from the command line as user (not root).

Step 3. latex filename.tex (it may prompt you to do this more than once)
Step 4. bibtex filename.aux
Step 5. mk4ht oolatex filename.tex (again, possibly you may need to do this more than once)

At this point, there will be various files in the directory that contained your original .tex file, but among them should be an .odt (OpenOffice Writer) file, which hopefully contains some decent approximation to what you had in LaTeX.

Worked for me! Hope it works for you.
Cheers, Eudemus

---

### Post by guerillero on 2009-04-14
Many thanks. I do respect people who not only find their way out by themselves, but also share the knowledge.

---

### Post by nvjopsddhapnv on 2009-07-14
Many many thanks to you

---

### Post by ohssss on 2010-02-03
Many thanks to your sharing. I haven't tried your method as it is a little complicated. I simply install the tex4ht from the repository in ubuntu 9.10 and use the commands:

latex test.tex
latex test.tex
latex test.tex
htlatex test.tex

The output file is called test.html, so I right click it and open it with openoffice. Most formating are also preserved except a minor alignment problem. It works like a charm. :)

---

### Post by ian.xerl on 2010-03-01
I did like ohssss and it works perfect, but the html file doesn't contain the bibliography nor any reference to it. What did I do wrong? The .bib file is in the same directory and I made bibtex run in the classical way. Can htlatex handle bibliographies?

---

### Post by legrandyon on 2010-07-22
Let me share my experience with this procedure: I have tried to follow all the steps from 
[http://www.cse.ohio-state.edu/~gurari/TeX4ht/mn-upgrade.html](http://www.cse.ohio-state.edu/~gurari/TeX4ht/mn-upgrade.html)
and they all went smoothly except that I never found any file
       bin/linux/tex4ht 
       bin/linux/t4ht  
for step 6. Not sure why (I found those file in .c but couldn't compile them with gcc to generate an executable). Therefore I kept the ones I had in my computer (Ubuntu 10.4).

Also the last step of the procedure, I had to do it as a super-user or the executable will not find xtpipes/:
> sudo mk4ht oolatex test.tex

Anyway if I follow all that I do obtain a .odt for my trivial test.tex file. 

When I tried to apply that to my real file, I would get an error for each and every column sign (:) used. Each time I hit "enter". The result is a successful .odt file (figures, layout, formulas) though 2 things don't work:
- tables
- references to the bibliography don't show a number but a [?].

Anybody understands how to improve on these problems?

---

### Post by phen on 2011-08-03
Hi!

The last couple of days I was looking for a good Latex-to-Word conversion. I was close to by some kind of a word plugin. But this is BY FAR the best way!

Figures, Equations, Hyperrefs, all included and WORKING!

Even tables work with the current versions shipped with ubuntu 10.4. (I did not install all the updates because this thread was from 2009, and I was right ;-)

Thanks anyway for sharing your experience. This made my day and the whole week! :guitar:

---

### Post by neoraist on 2011-08-30
That work for me too; I'd install tex4ht directly from ubuntu 11.04 repositories and using:

> Step 3. latex filename.tex (it may prompt you to do this more than once)
Step 4. bibtex filename.aux
Step 5. mk4ht oolatex filename.tex (again, possibly you may need to do this more than once)

works fine, I got a .odt document wich opens fine in libreoffice, by now, I only have tested formula editing.

Thank you

---

### Post by phen on 2011-10-05
Hey all,

after a while, I thought I should try out the upgrade mentioned by eudemus, as the version numberings didn't change over the last years. So I went through the update process and have to say that the results are even better with the updated version.

One problem is that the developers removed the bugfixes page
[http://tug.org/applications/tex4ht/bugfixes.html](http://tug.org/applications/tex4ht/bugfixes.html)

Since I use bibtex, too, this is a problem for me. Is somebody able to help me out with the files and maybe instructions?

thanks

bye

---

### Post by seo company on 2011-12-22
Thanks eudemus i joined this forum today finally just to say thanks for helping solve this conundrum conversion. Yes i will most likely add value back here. I do love ubuntu and so does most of the team i work with.

---

