---
title: "Is there any good application to organize PDF article files?"
date: 2007-08-23
forum: Education &amp; Science
---

### Post by tak1150 on 2007-08-23
This question has been somewhat asked before, but not to my satisfaction :)

As a researcher, I go through MANY PDF articles a day. I have been manually organizing them by categories. i.e.,

/home/me/Research/project1/sub-category/sub-sub-category/article.pdf
,etc

Which is a pretty good way to find the pdf files, but manually renaming the files so that I'll know which files to look at and manually placing these articles in the appropriate directories are getting to me these days.

Does anybody have a good system using either a script or app?
This page seems to suggest cb2Bib. Does anybody recommend it?
[https://help.ubuntu.com/community/UbuntuScience]("https://help.ubuntu.com/community/UbuntuScience")

Thank you!

---

### Post by melissawm on 2007-08-24
I use Tellico for the same purpose (math grad student) and I like it, but it's still cumbersome to add a new article.. However once it's done you can quickly recover any article by author, subject or title. If you find something else that works better, let us know.

---

### Post by earlycj5 on 2007-08-24
> **tak1150 said:**
> This question has been somewhat asked before, but not to my satisfaction :)

As a researcher, I go through MANY PDF articles a day. I have been manually organizing them by categories. i.e.,

/home/me/Research/project1/sub-category/sub-sub-category/article.pdf
,etc

Which is a pretty good way to find the pdf files, but manually renaming the files so that I'll know which files to look at and manually placing these articles in the appropriate directories are getting to me these days.

Does anybody have a good system using either a script or app?
This page seems to suggest cb2Bib. Does anybody recommend it?
[https://help.ubuntu.com/community/UbuntuScience]("https://help.ubuntu.com/community/UbuntuScience")

Thank you!

cb2bib or Referencer which was just discussed here recently in another thread on organizing PDFs (currently the sixth topic in the Science and Education Index page). [http://ubuntuforums.org/showthread.php?t=503365](http://ubuntuforums.org/showthread.php?t=503365) ;) 

cb2bib seems to do a bit better at recognizing the data in the PDF but Referencer is more of what I'd like to use.

---

### Post by miesnerd on 2009-04-25
> **tak1150 said:**
> This question has been somewhat asked before, but not to my satisfaction :)

As a researcher, I go through MANY PDF articles a day. I have been manually organizing them by categories. i.e.,

/home/me/Research/project1/sub-category/sub-sub-category/article.pdf
,etc

Which is a pretty good way to find the pdf files, but manually renaming the files so that I'll know which files to look at and manually placing these articles in the appropriate directories are getting to me these days.

Does anybody have a good system using either a script or app?
This page seems to suggest cb2Bib. Does anybody recommend it?
[https://help.ubuntu.com/community/UbuntuScience]("https://help.ubuntu.com/community/UbuntuScience")

Thank you!


Wow. You and I are on the same page. Fortunately, for you, I've been working towards this end. Im currently working on making my own version of ubuntu for scientists: ubuntu for scholars.

To answer your question more directly, though, I use a combination of packages to manage the bazillions of PDF's I go through.
Bibliography wise, managing PDF's can be done nicely thru Referencer.
Remembering what PDF's you accessed and when can be done by tweaking an awesome program, nemo (the non-file file manager).

---

### Post by miesnerd on 2009-04-25
ps the plan for my version of ubuntu (which I've called both ubuntu for scholars and ubuntu for social scientists) is to include a collection of bibliographic and statistics tools, of which cb2bib is planned to be included.

---

### Post by UbuWu on 2009-04-27
Zotero is pretty nice. I don't think it places pdf's in different directories, but it does do renaming. Finding back something from within zotero is a breeze. Also you can add comments, annotations etc.

---

### Post by neoflight on 2009-04-27
[Referencer]("http://icculus.org/referencer/") is a good one. 

Also [this]("http://ubuntuforums.org/showthread.php?t=379858") thread

Also see [Jabref]("http://jabref.sourceforge.net/"). May be helpful in collecting metadata from PDF's

---

### Post by earlycj5 on 2009-04-28
[http://www.mendeley.com/](http://www.mendeley.com/)

---

### Post by xadder on 2009-04-28
+1 for jabref

I like having the "database" in a plain ascii file. Excellent for LaTeX users, but also for anyone I think.

---

### Post by earlycj5 on 2009-04-28
> **xadder said:**
> +1 for jabref

I like having the "database" in a plain ascii file. Excellent for LaTeX users, but also for anyone I think.

I've tried JabRef, it's a great bibliography manager but it's not as good at managing PDFs as Referencer or Mendeley (for me), so no, it's not excellent for anyone.  It hasn't been what I want/needed.

---

### Post by bubblehead74 on 2009-04-29
Try [I, Librarian]("http://bioinformatics.org/librarian"). If you use PubMed, I think it is helpful.

---

### Post by samden on 2009-05-16
+1 for Zotero, you can place the .pdfs wherever you like and link to them from it. Great for getting references from web-based sources too.

---

### Post by Shonkin57 on 2009-12-09
A slightly different question re PDF organization.

Does anyone know of a way to auto-generate a simple html index page from a folder (and some sub-folders within it) filled with PDF books?

I am trying to build a Christmas present using PDF books -- which one could browse from the CD or DVD using a web browser. The books are already sorted by me into rough categories, but I want their titles individually links to... and there are a LOT of books.

The file tree as an example might look like this:

[Root CD folder] > [Xian-Books] > [Theology] / [History] / [Xian-Rightwing] / [CSLewis]

And so on... more subfolder levels might occur under, for instance, [Xian-Rightwing] > [Falwell] / [Focus-on-Family] / [Opponents-Of]

The ideal would be if the program made a master index page from the root, and a new page for each subfolder and sub-subfolder, all with the PDF books in that folder listed.

Not asking much, am I?!:popcorn:

---

### Post by tgalati4 on 2009-12-09
Super cheesy way to do it:

Open a new tab in firefox (Control-T)

file:///home/Shonkin57/Projects/1000_Books_to_Read_Before_I_Die/Authors_A

File save as html.

Rather than create an html file, just put a README.txt file in the top level directory with instructions on how to do the same.

You can also put an autorun script that displays a similar message.

---

### Post by Shonkin57 on 2009-12-10
Well, another kludgy way to sorta do part of the job anyway is this (pointed out to me by a face book friend). Go to each directory and sub-directory, and then from a linux command line:

dir > index.txt

This of course generates a document 'index.txt' (or whatever other name I use will work) listing every document and directory name in that folder.

I could presumably then use the text so generated in an html editor, linking it manually title by title to the documents in the folder.

Not really as easy as I wanted, though if nothing else comes up to auto-generate not only the dir but also the links in an html doc... I guess this would have to do.

---

### Post by Shonkin57 on 2009-12-10
> **tgalati4 said:**
> Super cheesy way to do it:

Open a new tab in firefox (Control-T)

file:///home/Shonkin57/Projects/1000_Books_to_Read_Before_I_Die/Authors_A

File save as html.

Rather than create an html file, just put a README.txt file in the top level directory with instructions on how to do the same.

You can also put an autorun script that displays a similar message.

That just generates an empty html file, doesn't it? Maybe I messed it up, but if not I'm trying to get (in linux or even in Winduhs via an Ubuntu VirtualBox session) it to do two things:

1. Pull all the file names, record them as text...

2. and link those text tags w/ html code back to the files so named -- creating a single html file for each folder.

I don't mind having to repeat the command or commands for each folder separately, as long as an index file as described is generated for each folder.

REALLY lazy of me, I realize. But there are a *lot* of books. And so little time...

Thanks for helping.

---

### Post by tgalati4 on 2009-12-10
Just create one html file (perhaps index.html) and put it in the root directory of the CD.  Then write an autorun script to launch the browser with index.html.

When index.html opens it points to the files on the disk. 

The challenge is to get relative links working since you want it to work on Mac and Linux, and, well, even Windows.

---

### Post by Shonkin57 on 2009-12-10
> **tgalati4 said:**
> Just create one html file (perhaps index.html) and put it in the root directory of the CD.  Then write an autorun script to launch the browser with index.html.

When index.html opens it points to the files on the disk. 

The challenge is to get relative links working since you want it to work on Mac and Linux, and, well, even Windows.

I get that. But I'm talking about auto-generating the CONTENT of the index page instead of me having to input it all myself, with either an html editor or by hand. I have one friend who's a SED geek, and he'd just write some impossible script and wham-o the thing would autogenerate a text file with all the html tags, file locations and names, and text needed.

That is what I'm looking for... the content of the index page, auto-generated. Not merely an index page.

Thanks again for your continued interest in the problem!

---

### Post by Shonkin57 on 2009-12-10
Conceptually, in fact, I can sorta see how the program would work.

One would start it in the root of the folder / directory one wanted the index.html file generated.

The program would auto-catalogue all the files into a text file.

It would next (or simultaneously) link each file name in the text file via html tags to the PDF file so named.

If I opened the result in a browser, it would have each pdf book title and I could click on that title and adobe reader (or its equivalent) would open said book.

Sounds so simple, eh?

Ha.

---

### Post by ErikEnsing on 2010-07-15
Dear all,
the easiest way to organize your life science articles is to use [www.linkedpapers.com]("http://www.linkedpapers.com").
LinkedPapers uses the Pubmed database, therefor search results are identical.
However, LinkedPapers in addition offers you the ability to tag your articles of interest right away. Tagged articles will be stored in your personal bookshelf.
It's thé most inuitive way of organizing your articles, just try it, I'm sure you will like it.
Very best wishes,
Erik

---

