---
title: "Does LaTeX matter for typeset manuscripts?"
date: 2007-02-02
forum: Education &amp; Science
---

### Post by cinnabar on 2007-02-02
I just submitted my first manuscript using LaTeX and have mixed feelings about using it the future. Of course I had to spend time learning how to use it but we'll ignore that for the time being. FYI, I used a mix of Kile and WinEdt (a windows program) in conjunction with JabRef to complete it. Here's my basic opinion:

Things that are easier with LaTeX:
1) I was able to create macros to automatically set up superscripts and subscripts for commonly used terms (e.g., when I type O3, the program automatically converts it to O$_{3}$). Big time saver. However, OpenOffice can be set up to do the same thing.
2) Never had to worry about fonts, sections, etc. However, this doesn't really matter to me. All of my manuscripts are typeset by our publications group, if it's a government report, or by the journal publisher.
3) Never had to worry about keeping track of table and section numbers. However, I did do my figure numbers by hand (see below). 
4) Automatic references. Freaking great and much less expensive than EndNote.

Things that are more difficult in LaTeX:
1) Tables are difficult to create, especially if you don't know exactly what you want. I ended up making all of them in Excel first, then "translating" that table into LaTeX by hand. I was not amused by the utilities that convert excel tables to LaTeX; the output code was ugly and confusing.
2) I had a difficult time being able to output an acceptable manuscript with tables, figure captions, and figures at the end of the manuscript as is required for every journal I've dealth with (I am a geochemist). I found one package to help (can't remember the name, sorry) but I still ended up add figure numbers by hand and keeping the figures entirely seperate from the LaTeX file (i.e., I just attached pdf's of the figures after I made my final output from LaTeX as a pdf.
3) It's difficult to read the raw LaTeX for purposes of editing. I usually had the pdf and the LaTeX editor open on oppposite screens so I could read the pdf and modify the code. However, when I only have 1 monitor (like I have at home) this is cumbersome.

Things that could go either way:
1) Although I was the primary author, I had 7 co-authors, none of which use LaTeX. It wasn't that hard inserting their text, which was written in Word, as I had to re-write much of it anyway. Also, getting comments wasn't too bad. I have Adobe Professional and was able to generate editable pdf files to send out to them so they could provide comments. However, I am not aware of a way to do this in Linux (I use a PC at work).

Granted that my LaTeX-based manuscript is more attractive than any other manuscript I've ever written. But given that everything I'm likely to create will be typeset, does it even matter? I'm curious what others think about this, especially those of you that have been publishing in journals using LaTeX for some time.  I'm about ready to start another manuscript and would any appreciate any input on the matter.  Thanks.

---

### Post by anoir on 2007-02-03
Try LyX. It is a WYSIWYM front end for LaTeX. I use LyX for virtually everything comfortably.  You do not need to memorize all the details of LaTeX (but if you know LaTeX better, you'll become more productive with LyX). I also do not have any problem with inserting figures and references.

LyX takes care of generating tables as well. gnumeric can export spreadsheets to tex files. R also has a good support for LaTeX.

Whether you should use LaTeX is a difficult question to answer. The most important reason I use LaTeX/LyX is its ability to produce beautiful mathematical expressions. If you do not use math intensively, then there is no compelling reason for you to learn LaTeX. In fields where math is an essential part of study, LaTeX IS the standard format for manuscripts. All the professors I talk to use either manual LaTeX editing, Scientific Word, or LyX. Academic journals accept tex files as their most preferred format.

---

### Post by parktownprawn on 2007-02-03
The fact that everyone in my field (high energy physics) uses latex is great. Almost everyone releases their preprints online (to arxiv.org ). For  papers after 1992 I never have to go to the library (or log onto some web site) to look in a journal - i can just look at the preprints. I can even download the latex source of other peoples papers and use their formula in my papers. Further more papers are accessible months before they would have been if we had to wait for them to be typeset, refereed etc.  It makes evil publishers like Elsevier increasingly irrelevant.

---

### Post by parktownprawn on 2007-02-03
Hmm - i guess i went on a political rant without answering any of your questions.

Some things that might help you:

1. you can produce a pdf file directly from a latex file using the command pdflatex.

2. you can convert a dvi -> ps -> pdf  using the comands dvips and then ps2pdf 

3. Yes tables and figures can be irritating - i find the package epsf adequate for figures. you might also find the package graphicx useful

4. I know the command 

\begin{figure}[p]
.......
\end{figure}

will at least put your figure on its own page - not sure how to force that to be at the end of the document

5. Its a bit of a pain to set up but getting forward and reverse search working between the latex source and a dvi file makes editing much easier. (see [http://xdvi.sourceforge.net/inverse-search.html)](http://xdvi.sourceforge.net/inverse-search.html)). You can just click on  the dvi file and it jumps back to the right place in your editor.

6. I like lyx but none of my collaborators do so I always end up having to work with the latex code. I've just started using Texlipse ([http://texlipse.sourceforge.net/](http://texlipse.sourceforge.net/)) which is a plugin for eclipse as my latex editor. Its problably over kill to use eclipse for editing latex but i like it. One thing i liked was that forward and reverse search worked pretty much out of the box on texlipse. also since its a java app you can use it on your windows or linux machines. and unlike something like winedt its free. oh and it has a nice utility for typing up tables.

---

### Post by WebDrake on 2007-02-03
> **cinnabar said:**
> 2) Never had to worry about fonts, sections, etc. However, this doesn't really matter to me. All of my manuscripts are typeset by our publications group, if it's a government report, or by the journal publisher.

It is, however, convenient from the point of view of letting you concentrate on the logical structure of the document.  In WYSIWYG environments there's still too much of a temptation to mess around with fonts *even when you shouldn't*.  Recently, helping out some friends who were planning on submitting to Nature, I found they'd been doing all sorts of things to make their document "look nice" even though the only thing you are supposed to do is use their paragraph styles.

In other words, LaTeX helps to some extent to save you from colleagues who don't read the manuscript style guidelines. :p

> **cinnabar said:**
> 4) Automatic references. Freaking great and much less expensive than EndNote.
Have you become familiar with BibTeX?  If not I strongly recommend you to.  It assists still further in making easy the construction of paper bibliographies.

> **cinnabar said:**
> Things that are more difficult in LaTeX:
1) Tables are difficult to create, especially if you don't know exactly what you want. I ended up making all of them in Excel first, then "translating" that table into LaTeX by hand. I was not amused by the utilities that convert excel tables to LaTeX; the output code was ugly and confusing.

Tables are a bit of a pain.  I don't know if there's any handy interfaces that let you elegantly construct a table.  Arrays in equations can also be an issue.

> **cinnabar said:**
> 
2) I had a difficult time being able to output an acceptable manuscript with tables, figure captions, and figures at the end of the manuscript as is required for every journal I've dealth with (I am a geochemist).
It might be worth inquiring whether that convention applies to LaTeX documents.  For example the Physical Review family of journals seem happy to accept documents with figures "in docu".  Many journals' LaTeX classes also provide the possibility to switch between a "neat" view which approximates the journal style and an "preprint" view that outputs in a manner (double-spaced, single-column, large text....) convenient for editorial overview.  With Word, if you put the figures in one place they're stuck there.

I presume you tried putting the figure list after all the document text, and using \begin{figure}[b] to try to place the figure at the bottom of whatever page it was on...?  See [http://www.andy-roberts.net/misc/latex/latextutorial6.html](http://www.andy-roberts.net/misc/latex/latextutorial6.html)

> **cinnabar said:**
> 
3) It's difficult to read the raw LaTeX for purposes of editing. I usually had the pdf and the LaTeX editor open on oppposite screens so I could read the pdf and modify the code. However, when I only have 1 monitor (like I have at home) this is cumbersome.

Things that could go either way:
1) Although I was the primary author, I had 7 co-authors, none of which use LaTeX. It wasn't that hard inserting their text, which was written in Word, as I had to re-write much of it anyway. Also, getting comments wasn't too bad. I have Adobe Professional and was able to generate editable pdf files to send out to them so they could provide comments. However, I am not aware of a way to do this in Linux (I use a PC at work).

There are WYSIWIG-esque LaTeX editors, which will let people type stuff more easily.  Whether they produce good LaTeX output, I'm not so sure.  Then again, if your manuscript really is pretty, and it really makes the bibliography etc. so much easier, perhaps you could persuade them to learn .... ? :)

> **cinnabar said:**
> Granted that my LaTeX-based manuscript is more attractive than any other manuscript I've ever written. But given that everything I'm likely to create will be typeset, does it even matter? I'm curious what others think about this, especially those of you that have been publishing in journals using LaTeX for some time.  I'm about ready to start another manuscript and would any appreciate any input on the matter.  Thanks.
"Pretty" is in some ways the less important part of LaTeX, unless you want to put your paper on a preprint archive or circulate among colleagues.  (One friend in neuroscience bemoaned the fact that journals in this field insisted on double-spaced, figures-at-the-end Word documents: reading them as a reviewer would be so much easier if the journal could pass them on, as you can with LaTeX, in a form somewhat resembling the journal's output.)  It can be *very* convenient for estimating how your paper will look in final output, and structuring/pacing it accordingly.  That said, not all journals have a nice associated LaTeX class for this purpose.

What is *really* important about LaTeX is that it allows you to write a very, very well-structured document that can be easily translated between many appearances depending on what is needed.  This is why it's so useful to academic publishers.

---

### Post by WebDrake on 2007-02-03
> **parktownprawn said:**
> 4. I know the command 

\begin{figure}[p]
.......
\end{figure}

will at least put your figure on its own page - not sure how to force that to be at the end of the document

D'oh!  I forgot that option when I was writing my long reply.  Yes, that should work.  Put all the figure-declaration text at the very end of the document and then use \begin{figure}[p], and it should put everything on separate pages at the end.  Mind you, it may still depend on the style class you're using.

---

### Post by Typhoon on 2007-02-03
I'm  a little bit of an odd man out here since I write legal textbooks. I have been using LaTeX together with Emacs + Auctex + Reftex for writing even when the publisher resets the whole thing.

I use it for several reasons:

1 I need multiple indexes: table of cases, table of statutes as well as an ordinary index

2 I use lots of cross-references - Reftex is fantastic for this

3 Good outlining facilities - back in the old days I used Thinktank and Grandview

4 (This relates to the clutter problem): the combination lets you "hide" most of the LaTeX markup if you want. It does make it easier to proofread.

In short, I have never seen any combination that gives such good author support.

---

### Post by Typhoon on 2007-02-03
Forgot to mention that I am in the process of self-publishing a cookbook written by my wife. I used LyX for typesetting and layout. 

Setting up a cookbook is considerably more complicated than most of the stuff I write. Ingredients lists, instructions, line drawings all need to be positioned.

LyX did a great job. I doubt that I could have done the job in the time available with anything else.

Typhoon

---

### Post by cinnabar on 2007-02-04
Parktownprawn - Thanks for your input.  Yes, I use pdfLaTeX all the time (I don't see the utility in making a dvi file).  However it is not an editable, commentable file unless I open my pdf in Adobe Reader Professional and convert it as such.  If I was using Kubuntu only I am not aware of a way to provide an editable file for comments to my non-LaTeX using co-authors.  I have tried latex2rtf, but haven't found the results suitable (no offense to the fine developers of the latex2rtf tool).

> **WebDrake said:**
>  Have you become familiar with BibTeX? 
Yes!  BibTeX is almost enough of a reason in and of itself to use LaTeX.  I am really impressed with the JabRef program for working with and exporting BibTeX references. 

> **WebDrake said:**
>  It might be worth inquiring whether that convention applies to LaTeX documents.  For example the Physical Review family of journals seem happy to accept documents with figures "in docu".  Many journals' LaTeX classes also provide the possibility to switch between a "neat" view which approximates the journal style and an "preprint" view that outputs in a manner (double-spaced, single-column, large text....) convenient for editorial overview.  
Because I would guess than <<5% of scientists in my field use LaTeX, I suspect by proving figures "in docu", it may confuse and/or possibly irritate reviewers.  If there is a command for generating "neat" view using the elsart.cls document class (for Elsevier Journal articles), I'd love to know about it.

> **WebDrake said:**
> There are WYSIWIG-esque LaTeX editors, which will let people type stuff more easily.  Whether they produce good LaTeX output, I'm not so sure.  
I used LyX for a very short time.  It's worth looking into because I can use it on all of computers (I have a PC, Mac, and 2 Kubuntu machines between work and home).  I'm curious to know how clean the code it produces is.  I originally gave up on it because of the command it was using for generating subscript and superscripts was not what I wanted (sorry, I no longer remember the exact issue).

> **WebDrake said:**
> What is *really* important about LaTeX is that it allows you to write a very, very well-structured document that can be easily translated between many appearances depending on what is needed.  This is why it's so useful to academic publishers.
I will admit that I once had convert a Word manuscript from an Elsevier style to a American Geophysical Union style; that took about 2 days.  

Typhoon - Thanks for your input on your combination.  However I am not an Emacs fan (not going there now) but I hope that your input will hope someone else!  Your comment about the utility of LaTeX in books is a good point.  However, I finished the closest thing to a book (my dissertation) I ever expect to write, a few years ago.  I would love to see a cookbook written in LaTeX though.  Did you have to make your own style?

One last point.  I recently updated by CV using LaTeX and am really blown away by how good it looks relative to other Word and OpenOffice versions I have previously made.  Because the use of LaTeX is rare in my field it may help getting my job applications more noticed than others.

---

### Post by WebDrake on 2007-02-04
> **cinnabar said:**
> Because I would guess than <<5% of scientists in my field use LaTeX, I suspect by proving figures "in docu", it may confuse and/or possibly irritate reviewers.  If there is a command for generating "neat" view using the elsart.cls document class (for Elsevier Journal articles), I'd love to know about it.

If you download the complete range of Elsevier files from [http://tug.ctan.org/tex-archive/macros/latex/contrib/elsevier/](http://tug.ctan.org/tex-archive/macros/latex/contrib/elsevier/) you will find that as well as the standard elsart.cls, there are three others---elsart1p.cls, elsart3p.cls and elsart5p.cls---which provide journal-like display.  The first is for one-column journals (e.g. Physica A), the latter two are two-column formats (e.g. some of the neural networks journals).  You can also get the bibliography styles from [http://tug.ctan.org/tex-archive/biblio/bibtex/contrib/elsevier/](http://tug.ctan.org/tex-archive/biblio/bibtex/contrib/elsevier/) (confusingly, they both offer you a complete download with the same filename, elsevier.zip, but their contents are different).

You might want to make use of a times font to get the look perfect.  Try \usepackage{mathptmx}.

I also decided to grab one of my old papers and try inserting the \begin{figure} .... \end{figure} stuff at the end, with [p] options---and indeed it places them at the end as your journals require.  So fear not about that.  The only issue may be whether the journal wants the captions separate from the figures.

---

### Post by Typhoon on 2007-02-04
Re Cookbook:

I used the Memoir class, mainly because it is so configurable. In the event, I didn't need to do much - I changed the default Chapter styles and did some minor fiddling with the before and after Chaptertitle.

<Shameless plug> The book is called "The Restless Minestrone" and you can see some preview pages at [http://web.aanet.com.au/sage](http://web.aanet.com.au/sage) BUT NOT YET. The book is currently with the Australian National Library awaiting pre-publication cataloging. I expect to have the samples and the web site up sometime next week. </Shameless plug>

LyX was really good for this. I made a lot of use of "boxes" to get the layout right.

And, to answer another question above, exporting LaTeX from LyX produced remarkably clean code.

I don't use LyX in most of my work because of the need for multiple indexing. LyX just doesn't handle that well. In addition, I index and Xref according to paragraph numbers. This is not hard to implement in LaTeX, but it is not simple in LyX. Using paragraph numbers allows you to complete all indexing tasks independently of the final typesetting layouts.

Cheers,
Typhoon

---

