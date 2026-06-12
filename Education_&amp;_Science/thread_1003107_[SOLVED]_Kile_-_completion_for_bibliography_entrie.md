---
title: "[SOLVED] Kile - completion for bibliography entries"
date: 2008-12-05
forum: Education &amp; Science
---

### Post by tekkenlord on 2008-12-05
Hello all. Does anyone know if there is a way to configure Kile such that when I type "\cite{" it will popup a list of the authors I have in a bib file? 

As an example, if my bib file has a single entry like:

@ARTICLE{tekkenlord:2008
  author = {AUTHOR_NAME},
  title = {TITLE},
  journal = {JOURNAL_NAME},
}

then ideally I would like to type in Kile

"\cite{tek" 

and get the completion of the word "tekkenlord:2008" which is the key entry for that article?

I have done an extensive google search and found that this feature supposedly is already implemented, but it does not work for me. 

Another suggestion ( [http://www.linuxquestions.org/questions/linux-desktop-74/kile-bibtex-507168/]("http://www.linuxquestions.org/questions/linux-desktop-74/kile-bibtex-507168/") ) was to include the bib file in the same directory of the tex file, this did not work either.

If any has this feature working, I would greatly appreciate his help! Thanks in advance.

---

### Post by tekkenlord on 2008-12-05
Never mind, I found the solution. For those interested, these are the steps I followed:

1) Create a new Project
2) Copy or create a link to the bib file in the directory that the Project was created
3) Add this link to the currect Project

That's it. Now, just type \cite{}, move te cursor between the curly brackets and press Ctrl-Space to get a full list of your key entries.

---

### Post by morgengenuss on 2009-02-09
thanks a lot! that did the trick for me too!
(i switched to kile from a different editor, therefore didn't create a project-file in the first place)

---

### Post by Mander on 2009-02-22
This still isn't working for me and I don't know why.  The .bib file and the project are in the same directory, and always have been.  I recall it working before but I had to reinstall Ubuntu, and ever since I haven't been able to get this to work.

Are you two using Gnome or KDE?  I wonder if that has anything to do with it.

---

### Post by tekkenlord on 2009-03-05
Sorry for the late reply, I have not been checking the thread lately. I am using KDE 3.5.10. Strange that it doesn't work for you...

---

### Post by conradlee on 2009-03-15
This auto-complete feature is also not working for me.  I am using KDE 4.2.  I created a project, in which my bib-file is included, but the bibtex entries to not pop up as options.

---

### Post by tekkenlord on 2009-03-22
For those who have problems with the auto-completion feature: 

You have to make sure of three things:

1) You have to create a new project

2) You must copy or link your bib file to the same directory as your project

3) Include the package "natbib" (\usepackage{natbib}) and finally insert the command \bibliography{your_bib_filename}

Please try that and post back.

---

### Post by Mander on 2009-03-26
Sorry, I haven't been paying much attention to this thread, either!

I've been using a project in Kile (using natbib and keeping the bibtex file in the same directory) for a long time, but just to see what would happen I created a new project (with the same files).  Still no dice.  

But I think I may have figured out the problem.

My academic supervisors complained when I gave them a draft with all of the bibliography attached, so I have been using the \nobibliography command so that the citations show up in the text where they are supposed to, but the list at the end isn't generated.  I just tried changing this back to \bibliography and now it works.

Although I swear I tried that before and it didn't work, so it's possible that creating a new project also magically solved the problem.

Anyway, it works now!

---

### Post by SorryGoFish on 2009-03-30
Another thing to note is in your Settings (Kile>Complete) you have to type the number of characters set in "Thereshold."

---

### Post by tigru on 2009-08-21
Hi - I have an additional question concerning the same subject: 

completion works fine for me, but I miss some commands as I use biblatex.

So I added 

\textcite[text]{keylist},
\textcite{keylist}, 
\citep{keylist} 

and a couple of others to  latex-document.cwl.

The effect is that the commands are now shown as proposals for completion but no keylist appears. Is there another file where I have to create a link between command and the keylist? 

Thanks in advance for any kind of help

tigru/juergen

---

### Post by tigru on 2009-08-21
Wow... I found some hint on dante.org and downloaded the files biblatex-dev.cwl and biblatex.cwl. After restoring my latex-documents.cwl (which is now exactly as before my "operation"), I now really have some new commands working. But unexpectedly all biblatex-commands seem to work perfectly (including offering me a keylist of Literature keys) except for \textcite. Does anybody know this "bug" (or whatever it may be?)

Thanks in advance

tigru/Jürgen

---

### Post by cathalcummins on 2009-10-19
I'm using Kile 2.0.1 to PDFlatex my documents. I use kbib to manage my references.

My references are contained in:

/home/cathal/Documents/College/LaTeX/BibTeX/References.bib

Here is an example of a typical .tex document


%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

\documentclass[a4paper]{report}
\usepackage{graphicx}
\usepackage{natbib}
\usepackage{subfigure}
\usepackage{polynom}
\usepackage{graphics}
\usepackage{wrapfig}
\usepackage{amssymb}
\usepackage{amsmath}
\bibliographystyle{plain}


\begin{document}


Some things\cite{Szekeres2004} need to be referenced so the individuals get credit for their work.


\bibliography{/home/cathal/Documents/College/LaTeX/BibTeX/References.bib}
\end{document}

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

If I run my Quickbuild;

PDFLaTeX >> BibTeX >> PDFLaTeX >> PDFLaTeX

I get the "Finished  with exit status 2" error. However, if I run the regular PDFLaTeX command (from the toolbar) the references come up and no errors.

I don't understand why BibTeX is even needed...

Also, I have tried the following;

1. Download + copy bibtex.cwl,bibtex-dev.cwl into the relevant folder and add these to autocomplete menu.

2. Copy References.bib into the TeX folder.

3. Create a "Project" and "Add files" and choose "References.bib".

And *still* can't get the autocomplete to come up on citation. I know it's not a big deal, but I've spent a good few hours on this now and, frankly, I'm determined to get it working!

Any ideas, particularly on the autocomplete thing...?

All the best,

---

### Post by markus.readus on 2010-02-09
I'm using Kile 2.0.83 on ubuntu, and also can't get autocomplete working for my \cite{xxx} commands. Works fine for everything else, but the only place it would be genuinely hugely useful is with the cite commands - my bibliography file is huge and searching through it is cumbersome. In previous versions of kile I've had it working briefly here and there, but its never really worked particularly well for long. I've been looking around online, and the only solutions I keep finding entail adding a symbolic link to the bibliography file from my local directory (where the .tex file is located), adding it to the same project as the tex file, and refreshing the tree. Still nothing though.

Does anyone have any idea how to get this feature working? I can't see why it would be such a problem, winedt used to do it without even blinking!

---

### Post by turiontzukosson on 2010-08-23
You have to use \bibliography{mybib.bib} somewhere in the project. And you have to enter the file name literally. It is not possible to use a command like \newcommand{\pathtomybib}{mybib.bib} and then \bibliography{\pathtomybib}.

---

