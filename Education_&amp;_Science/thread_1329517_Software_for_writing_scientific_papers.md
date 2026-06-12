---
title: "Software for writing scientific papers?"
date: 2009-11-17
forum: Education &amp; Science
---

### Post by Campitor on 2009-11-17
Hello All:

  I was wondering if any of you have come across a good software for writing scientific papers.  I was at a conference and someone suggested [Text Block Writer]("http://softwarebybrian.com/cms/content/view/20/2/"), which only runs under Windows.  

  I've always writen science papers with what I call modular-writing.  I tend to write tid-bits of information while reading papers, talking to friends or collegues.  These are ideas that pop into my head. Some are crude and require lots of editing before adding them to the paper. Others come out of the ether as perfectly formatted paragraphs and can be included into the paper immediately. These information snippets, up until now, have been all in a single file (text file) and moving them around the "master document" involves a lot of copy-paste.  I really like the idea of Text-Block-Writer, where ideas are handled like notes or cards.  But the fact that you can order them and export them into a single threaded  and cohesive work... is just wonderful  

  I don{t know if you guys write the same way, maybe because English is not my first language (as you probably have noticed) writing scientific papers from scratch just seems like an unsurmountable task. But sectioning the work has always seemed like a better way of doing things.

Any suggestions on ubuntu software that may match my writing style? 
Thanks in advance.

Camp.

---

### Post by XCan on 2009-11-17
For me, there is only latex, which actually should work very well with your style. For example, I wrote my thesis in separate .tex files and just called them in the main document in the correct order. I don't know which field you're in, but for physics, using anything but latex with the revtex templates or the occasional latex templates is just a waste of time and effort.

---

### Post by ahmatti on 2009-11-17
I second Latex. It takes care of numbering of headings, figures etc. automatically so its really easy to move your bits of text. The only problem for me is that not all Ag journals accept Latex submission.

---

### Post by apmcd47 on 2009-11-17
LaTeX is the text processor of choice for scientists - particularly of the computing variety.

Check out the ["See ALso"]("http://en.wikipedia.org/wiki/LaTeX#See_also") section of the LaTeX entry in WikiPedia for LaTeX editors if you prefer not to insert all the markup required for LaTex.

Andrew

---

### Post by Campitor on 2009-11-17
Thanks for the quick replies. I used latex and lyx a lot for my dissertation (actually wrote my dissertation on lyx).  But now I've moved more towards OO since collaboration with Lyx/Latex was just impossible.  Additionally, formating for journals in LaTeX or LyX is **almost** impossible in my field: Conservation Genetics of Tropical species.  Nevertheless, as of now, my modular writing occurs in text files, since they are very portable and easy to open in any platform (my laptop still has windows because of my wife...although now it's full of virus so she might want to move to lighter side of OS's).  Specifically,  I've been using KeepNote which is in the repositories...but it wont export into a single file that I can import into OO.

Don't get me wrong, I love LyX/Latex.  But all my papers are written in collaboration with authors abroad.  It was hard enough making them change to OO or google docs.  Latex is completely out of the question.  

Well, let's see if other people have other suggestions.  

Thanks

Camp.

---

### Post by samden on 2009-11-17
What about BasKet Note Pads? (sudo apt-get install basket) That would let you write each section as a note, then drag them round, in a pretty similar way to Text-Block-Writer.

You can export the finished product in html, which could be imported into openoffice.

---

### Post by Campitor on 2009-11-17
Thanks samden.  Basket note pads seems like the software I was looking for.  It does seem very cool.  Just one question (kinda of dumb question)> I always run gnome and this seems like a kde app.  Can I still run it? will I need to download the whole KDE environment?

Thanks.

---

### Post by spinoza666 on 2009-11-18
I just thought I should add that conversion from tex to odt is possible:

[http://ubuntuforums.org/showthread.php?t=1033441](http://ubuntuforums.org/showthread.php?t=1033441)

and from odt to tex by use of the writer2latex package.

I haven't tried this myself, but it seems you can use latex and still collaborate with odt/doc users.

---

### Post by PC_load_letter on 2009-11-18
> **Campitor said:**
> Thanks samden.  Basket note pads seems like the software I was looking for.  It does seem very cool.  Just one question (kinda of dumb question)> I always run gnome and this seems like a kde app.  Can I still run it? will I need to download the whole KDE environment?

Thanks.

Certainly not. I use Gnome all the time and my Latex editor of choice is Kile (a KDE app). What Kile does is install only the libraries it needs to run, most of them were QT3, QT4 related, it also installed okular since it's the app that Kile uses to open DVI files, you can change that later. I have never run across a KDE app that needed to install the KDE desktop, not yet :D

---

### Post by doas777 on 2009-11-18
well, there is this for computer science:

[http://pdos.csail.mit.edu/scigen/](http://pdos.csail.mit.edu/scigen/)

attached is the paper it generated for me

---

### Post by Campitor on 2009-11-18
> **PC_load_letter said:**
> Certainly not. I use Gnome all the time and my Latex editor of choice is Kile (a KDE app). What Kile does is install only the libraries it needs to run, most of them were QT3, QT4 related, it also installed okular since it's the app that Kile uses to open DVI files, you can change that later. I have never run across a KDE app that needed to install the KDE desktop, not yet :D

Thanks, I will install Basket right now.!!!!
I'll report how things go.

Camp.

---

### Post by gjatute on 2009-11-18
> **spinoza666 said:**
> I just thought I should add that conversion from tex to odt is possible:

[http://ubuntuforums.org/showthread.php?t=1033441](http://ubuntuforums.org/showthread.php?t=1033441)

and from odt to tex by use of the writer2latex package.

I haven't tried this myself, but it seems you can use latex and still collaborate with odt/doc users.

I experienced odt to latex and it doesn't work very well (I mean: a lot of cleaning and adjusting is needed... And I am quite experienced with latex). By the way I have the same problem: I just started to work in a "biology" environment and in this context the idea of latex is absolutely refused... A revolution is probably more needed than a software :-k

---

### Post by Campitor on 2009-11-18
> **gjatute said:**
> I experienced odt to latex and it doesn't work very well (I mean: a lot of cleaning and adjusting is needed... And I am quite experienced with latex). By the way I have the same problem: I just started to work in a "biology" environment and in this context the idea of latex is absolutely refused... A revolution is probably more needed than a software :-k

 I love revolutions :twisted:, but I don't think it is an easy task. 

 Well, I've given Basket a try and it looks very nice and similar to Text-Block-Writer.  I even  have four columns: Introduction, Methods, Results, Discussion.  The only problem I see is exporting to HTML, which doesn't do a good job and importing into OO will be a pain.  In this regard, it is similar to keepnote, which also has issues exporting to HTML.

Well, at least it's getting closer.  I can tweak with it until I find a way of exporting into html without all the images and tables.

Thanks for all the help

Camp

---

### Post by samden on 2009-11-18
If you just open the generated html file in Firefox and save as a text file, does that tidy it up at all? You might need to put it all in one column maybe.

---

### Post by booksnmore4you on 2009-11-18
Allow me to suggest [Zotero]("http://www.zotero.org/"), particularly the very stable beta version which enables the collaboration you're seeking.

---

### Post by Biochem on 2009-11-18
OO does support master documents where sections are in separate odt files and you can re-order them easily. And if you use the styles for you formating Image and table numbers are taken care off automatically.

---

### Post by NikoC on 2009-11-19
I already made the layout for my PhD manuscript using latex, but currently I'm leaning more towards Lyx (have written a couple syllabuses for student practical courses and it's quite nice, though some knowledge of latex is preferable).

---

### Post by XCan on 2009-11-19
What do you mean? Lyx is just a WYSIWYG editor built on latex. I would stick to your template. WYSIWYG is not optimal for writing, nor typesetting. I actually don't know what they're good for besides eyecandy. :p

---

### Post by ahmatti on 2009-11-19
Have you tried using restructured text or markdown? Their idea is a bit similar to latex, but both offer conversion to odt and latex.

---

### Post by ricky55 on 2009-11-19
> **Campitor said:**
> Hello All:

  I was wondering if any of you have come across a good software for writing scientific papers.  I was at a conference and someone suggested [Text Block Writer]("http://softwarebybrian.com/cms/content/view/20/2/"), which only runs under Windows.  

  I've always writen science papers with what I call modular-writing.  I tend to write tid-bits of information while reading papers, talking to friends or collegues.  These are ideas that pop into my head. Some are crude and require lots of editing before adding them to the paper. Others come out of the ether as perfectly formatted paragraphs and can be included into the paper immediately. These information snippets, up until now, have been all in a single file (text file) and moving them around the "master document" involves a lot of copy-paste.  I really like the idea of Text-Block-Writer, where ideas are handled like notes or cards.  But the fact that you can order them and export them into a single threaded  and cohesive work... is just wonderful  

  I don{t know if you guys write the same way, maybe because English is not my first language (as you probably have noticed) writing scientific papers from scratch just seems like an unsurmountable task. But sectioning the work has always seemed like a better way of doing things.

Any suggestions on ubuntu software that may match my writing style? 
Thanks in advance.

Camp.
I think Mek & Tosj today released Papers, a new application designed to revolutionize the way scientists deal with scientific papers.

---

### Post by earlycj5 on 2009-11-19
> **XCan said:**
> What do you mean? Lyx is just a WYSIWYG editor built on latex. I would stick to your template. WYSIWYG is not optimal for writing, nor typesetting. I actually don't know what they're good for besides eyecandy. :p

I'd hesitate to call Lyx a WYSIWYG, it's somewhere in-between a WSYWIG (MS Word, OOwriter) and Latex.  More of a front-end for Latex for the uninitiated.

I do prefer just using Latex but for the boss who wants to track changes, Lyx offers that so I use it.

---

### Post by XCan on 2009-11-19
Ah, indeed you are right. It's more one of those WYSIWYM editor iirc. :)

---

### Post by earlycj5 on 2009-11-19
> **XCan said:**
> Ah, indeed you are right. It's more one of those WYSIWYM editor iirc. :)

Yeah, I couldn't remember the term that they used, but that was it.

---

### Post by Campitor on 2009-11-19
> **samden said:**
> If you just open the generated html file in Firefox and save as a text file, does that tidy it up at all? You might need to put it all in one column maybe.

Yes.  you're right.  The multicolumn, although really neat, is not good for exporting. I will try and do separate pages for each section: Introduction, Methods, Results, Discussion.  Although using the 4 columns is nice because you can get a good idea of the hole paper.  I thinks this software is going to be very useful. Thanks.


> **booksnmore4you said:**
> Allow me to suggest [Zotero]("http://www.zotero.org/"), particularly the very stable beta version which enables the collaboration you're seeking.

I love Zotero...but I only use it as a reference manager. My notes are limited to papers.  I don't think is a good tool for my writing style.  But it is an invaluable tool for research. I'm also developing a bunch of citation-styles for the biological sciences. CSL is still a bit limited though.

> **Biochem said:**
> OO does support master documents where sections are in separate odt files and you can re-order them easily. And if you use the styles for you formating Image and table numbers are taken care off automatically.

Thanks for the suggestion.  Most of the time I don't do that much writing to warrant a full article.  Sometimes my notes are something like "Variation of inbreeding coefficients discussion goes here".  So a hole document for that sentence would be overkill.  Basket seems to be exactly what I needed.

> **ahmatti said:**
> Have you tried using restructured text or markdown? Their idea is a bit similar to latex, but both offer conversion to odt and latex.

No. Never heard of it. After some googling, it seems like a markup language similar (simplified) to HTML coding. Is that right?  I thought about this for a while and I think it would be really nice if one could develop a markup system (maybe based on xml) where you could just write a single document and markup sections (a section may be a line or a paragraph or multiple paragraphs) based on a structure like: <idea>, <intro>, <methods>, <discussion>, <important>, <bogus>, etc.  But these can be placed anywhere in the document, as ideas or paragraphs flow down randomly from the ether. Later on a compiler can put all these sections  in a specific order: Introduction, Objectives, Methods, Ideas, etc.  and export into html, text, or latex.  I don't know... maybe my ADD is just beyond help. Thanks for the suggestion.

> **ricky55 said:**
> I think Mek & Tosj today released Papers, a new application designed to revolutionize the way scientists deal with scientific papers.
Isn't this a Mac Application?

Thank you all for your comments and suggestions. ;)

---

### Post by ahmatti on 2009-11-20
> **Campitor said:**
> 

No. Never heard of it. After some googling, it seems like a markup language similar (simplified) to HTML coding. Is that right?  I thought about this for a while and I think it would be really nice if one could develop a markup system (maybe based on xml) where you could just write a single document and markup sections (a section may be a line or a paragraph or multiple paragraphs) based on a structure like: <idea>, <intro>, <methods>, <discussion>, <important>, <bogus>, etc.  But these can be placed anywhere in the document, as ideas or paragraphs flow down randomly from the ether. Later on a compiler can put all these sections  in a specific order: Introduction, Objectives, Methods, Ideas, etc.  and export into html, text, or latex.  I don't know... maybe my ADD is just beyond help. Thanks for the suggestion.



I haven't actually used either, but from what I have read they seem intresting. From what I read reStructuredText can be used to write a whole book with bibliography, tables and images and you can convert it to HTML, Latex or odt. Markup I guess is more for producing HTML documents. Stackoverflow has some anwers about the differences the  [http://stackoverflow.com/questions/34276/markdown-versus-restructuredtext](http://stackoverflow.com/questions/34276/markdown-versus-restructuredtext).

reStructuredText is a part of the Python docutils and is has been used to write the new Python documentation. I think the  quickstart guide makes it seem simple enough. [http://docutils.sourceforge.net/docs/user/rst/quickstart.html](http://docutils.sourceforge.net/docs/user/rst/quickstart.html) and intend to give it a try.

I don't think a program for reordering papers based on the section headers exists, but it should brr possible to create a parser to reorder  e.g  restructredtext or Latex document based on primary headings. EDIT: It looks like you might get what you want with docutils: [http://docutils.sourceforge.net/docs/dev/hacking.html#modifying-the-document-tree-before-it-is-written](http://docutils.sourceforge.net/docs/dev/hacking.html#modifying-the-document-tree-before-it-is-written)

---

### Post by Stan_1936 on 2010-04-25
> **ahmatti said:**
> ....reStructuredText can be used to write a whole book with bibliography, tables and images and you can convert it to HTML, Latex or odt. ...

> **ahmatti said:**
> Have you tried using restructured text or markdown? Their idea is a bit similar to latex, but both offer conversion to odt and latex.

> **gjatute said:**
> I experienced odt to latex and it doesn't work very well (I mean: a lot of cleaning and adjusting is needed......

_None of the so-called "converters" to LaTeX offer a solution_ that does ***_not_*** require extensive cleaning and adjusting.  Not even LyX.  And certainly not OpenOffice/MS Word.

**For journals, as was what the OP was interested in, forget about LyX....it'll butcher things!**  For other written material, LyX will do the job.

---

