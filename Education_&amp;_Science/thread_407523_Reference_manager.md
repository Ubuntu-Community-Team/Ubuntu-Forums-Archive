---
title: "Reference manager?"
date: 2007-04-12
forum: Education &amp; Science
---

### Post by NikoC on 2007-04-12
So I was just wondering what you people use as a reference manager for your scientific articles? At the university we have a nice piece of software but it is only available for windows. Are there any linux packages that are any good and if possible are compatible with Bibtex/Latex?

---

### Post by WW on 2007-04-12
[JabRef]("http://jabref.sourceforge.net/") is pretty nice.

---

### Post by NikoC on 2007-04-12
Thanks for the tip! I've installed JabRef and it looks indeed pretty complete to me, only downside is that menus do not show up when I have beryl as a window manager. I have to change to metacity to  be able to access them.

---

### Post by edsesq on 2007-04-12
I've run across this problem with a couple of other Java programs (jPicEdt) when running Compiz, so I think it's more of a problem with Java than with JabRef.

---

### Post by akniss on 2007-04-12
Bibus
[http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page](http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by kleeman on 2007-04-12
pybliographic

Nicer interface than jabref in my opinion but maybe not as featured.

sudo apt-get install pybliographer

---

### Post by NikoC on 2007-04-13
Thanks people, going to try them out today so I can make a selection.

---

### Post by Ken T on 2007-04-13
Hi,

Just spotted this thread re: reference manager after I submitted a very similar one... apologies. (It may be helpful to have a quick look at it, in order to help me with my question, though.)

I see you guys have suggested three such programs - Jabref, Bibus and Phybibliosomethingorother.

Do any of you guys have experience with Endnote? How do you think these compare with it (particularly the Cite While You Write function and interconnectedness with word processing program)? I'm hoping I can pick your brains to discover the best alternative for me, rather than downloading, installing and trialling all three for myself.

Thanks for your patience & help.
Ken.

---

### Post by akniss on 2007-04-13
If you want "Cite while you write" functionality, it will depend on what you use to write.  Bibus will work with MS Word on Windows, or OpenOffice Writer on Windows or linux.  I used Bibus/OOo for my PhD dissertation, and it worked like a charm.  I'm currently using Bibus with MS Word on a paper that i need to collaborate with several co-authors that use MS products.  Bibus seems to work equally well on linux or windows, Word or Writer.

Pybliographic works well with Lyx.  I tried this for a while before I decided that latex wasn't for me.

Jabref... I'm not familiar enough to know.  Maybe someone can chime in on that.

---

### Post by venik212 on 2007-04-13
I downloaded jabref from Softpedia, but it comes as a *.jar.  How do I install it?

---

### Post by kleeman on 2007-04-13
You need to install java e.g.

sudo apt-get install sun-java6-jre

and then find the executable (for the above package it is 

/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java 

then issue

/PATHTOJAVA/java -jar /PATHTOJABREF/JabRef-2.2.jar

I created a launcher on my gnome panel to do this....

---

### Post by venik212 on 2007-04-16
How do you create a launcher for that command line on KDE?

---

### Post by Ken T on 2007-04-17
> **akniss said:**
> If you want "Cite while you write" functionality, it will depend on what you use to write.  Bibus will work with MS Word on Windows, or OpenOffice Writer on Windows or linux.  I used Bibus/OOo for my PhD dissertation, and it worked like a charm.  I'm currently using Bibus with MS Word on a paper that i need to collaborate with several co-authors that use MS products.  Bibus seems to work equally well on linux or windows, Word or Writer.

Pybliographic works well with Lyx.  I tried this for a while before I decided that latex wasn't for me.

Jabref... I'm not familiar enough to know.  Maybe someone can chime in on that.

Thanks Akniss - much appreciated. I like the sound of Bibus being functional with both OO and  Word, so will give this a punt (even though my "fallback" will be using MS Office 2004 for Mac, I'm reasonably confident that it too will work).

My next aim will be to create my reference library in Ubuntu, so that it's accessible from Mac OS X (I'm running Ubuntu in a virtual machine on a Macbook laptop), but perhaps that's one for another forum... any ideas though will be appreciated.

Thanks again, 
Ken.

---

### Post by earlycj5 on 2007-04-18
I like to use kbib and cb2bib for extracting information from PDFs and some management.

---

### Post by Turjan on 2007-04-19
I'm still pretty curious whether anyone tried both, JabRef and Bibus, and can give some informed recommendation about the pros and cons.

---

### Post by hugmenot on 2007-04-20
Bibus is better integrated with OpenOffice and JabRef is good for LaTeX.

---

### Post by Turjan on 2007-04-20
Thanks. That was concise :). Looks like Bibus for me then.

---

### Post by aliennet on 2007-04-21
pybliographic: not vey fast but beatiful...I can't work with it
JabRef: the layout result orrible in Gnome but it is fast and good and integrated with lyx
I'd like a mix.

A piece of software good for which of us that have the hardisk full of pdf is Referencer ([www.getdeb.net](www.getdeb.net))

---

### Post by earlycj5 on 2007-04-22
> **aliennet said:**
> pybliographic: not vey fast but beatiful...I can't work with it
JabRef: the layout result orrible in Gnome but it is fast and good and integrated with lyx
I'd like a mix.

A piece of software good for which of us that have the hardisk full of pdf is Referencer ([www.getdeb.net](www.getdeb.net))


WOW, I was looking for something like Referencer a while back and couldn't find anything, this is great!  Thank you so much!!!

---

### Post by hugmenot on 2007-04-22
But of which use is Referencer when it retrieves only the last name of the first author?

Authors: EINSTEIN

Good grief!

---

### Post by earlycj5 on 2007-04-22
> **hugmenot said:**
> But of which use is Referencer when it retrieves only the last name of the first author?

Authors: EINSTEIN

Good grief!

What?  I just started fiddling around with it an hour ago, I'm afraid I don't understand your problem with it yet? :confused:

---

### Post by Mr Al on 2007-04-22
I'm a big fan of [Zotero]("http://www.zotero.org/"). It should have cite while you write functionality for OpenOffice sometime during this year, according to the developers.

---

### Post by hugmenot on 2007-04-22
> **earlycj5 said:**
> What?  I just started fiddling around with it an hour ago, I'm afraid I don't understand your problem with it yet? :confused:
I tried this app out on a folder with 167 pdfs. On a fraction of about 0.2 it found the DOI in the file and retrieved some info from crossref.org. The results were very poor. For example it only obtained the last name of the first author. Which is totally useless for citation.
Actually I much prefer the style of metadata tagging that JabRef uses in the recent versions. It tags the meta-information fields of a PDF with the proper data and also writes it properly to the Dublin Core section of the XMP header.
If only beagle would read that.

---

### Post by earlycj5 on 2007-04-22
> **hugmenot said:**
> I tried this app out on a folder with 167 pdfs. On a fraction of about 0.2 it found the DOI in the file and retrieved some info from crossref.org. The results were very poor. For example it only obtained the last name of the first author. Which is totally useless for citation.
Actually I much prefer the style of metadata tagging that JabRef uses in the recent versions. It tags the meta-information fields of a PDF with the proper data and also writes it properly to the Dublin Core section of the XMP header.
If only beagle would read that.

Gotcha.  That stinks.  Seems like it has promise, if it would work properly.  I really would like something that I can organize PDFs with like this.

---

### Post by frisket on 2007-04-23
You don't. You run run it with Java, eg $ java -jar /var/software/JabRef-2.2b2.jar (or whatever the version is). If you want to be able to use it in Firefox to capture downloadable .ris and .bib files, then create a script in ~/bin to say 

java -jar /var/software/JabRef-2.2b2.jar $1

and teach FF to run it.

---

### Post by tvor on 2007-05-01
I was looking for some referencing software which can fetch from internet libraries ..(it does not seem like [pybliographer]("http://pybliographer.org/") does, but [Zotero]("http://www.zotero.org/") project certainly got my attention. They have released support plugin for [Microsoft Word recently]("http://www.zotero.org/documentation/microsoft_word_integration") , hopefully close to support Open Office (sometime in 2007 according to the authors). This project is open source and free unlike End Note.

---

### Post by lngndvs on 2008-04-28
I've been messing about trying to find the ideal reference manager.  I've hit a bunch of them.  For what it's worth, I've posted a couple of blog entries on a crummy blog at fsworkingnotes.blogspot.com.  

I have tried to get into touch with the following:

   [LIST]
[*]kbibtex: really, really nice.  Can download pdfs.
[*]kbib: not as nice
[*]jabref:  excellent.  On a par with kbibtex, better on some things.
[*]emacs with bibtex mode:  cleaning up messes.
[*]cb2Bib:  Wow!  Have to install bibutils from scratch (on Hardy)  to use this fully.
[*]referencer:  doesn't integrate as well with bibtex.  Does interesting things.
[*]pybliographer:  Not as useful for me.
[*]tellico:  Not focused on bibtex or bibliography.
[/LIST]

Cb2Bib borders on magic.  I did find it necessary to install bibutiles from this site.  I had to compile it myself, because I could not find an Ubuntu or Debian package (Hardy).
 [http://www.scripps.edu/~cdputnam/software/bibutils/bibutils.html](http://www.scripps.edu/~cdputnam/software/bibutils/bibutils.html)

Each of these has its own strengths, especially kbibtex, jabref, and cd2Bib.  Some other interesting directions include NeuroScholar and Zotero.  I haven't grokked Zotero yet, but in combination with cb2Bib, I am able to scarf bibliography data.  Kbibtex is quite nice.

This is obviously a field with active development moving on several different fronts.  

Alan

---

### Post by xadder on 2008-04-28
I've also just discovered jabref, and am now a big fan. It gives me easy/instant access to all my pdfs, allows very easy keyword additions and usage, and keeps everything in a nice simple text file which I can look at and edit with good old vi when I feel like it.

I tried out referencer a while ago, and quickly found problems. It sometimes finds the wrong doi and thus assigns the wrong file information.


I'm a heavy LaTeX user and thus jabref is perfect. It does allow input/output of endnote and the like. Input seems to be flawless, but I haven't tested how output (since I try to avoid Word and Oooffice).

---

### Post by mnajem on 2010-02-16
i was unable to fetch PDF/lists from IEEE and Citeseer in jabref. Is there any way to figure out what went wrong?

---

### Post by kokoshmusun on 2010-02-17
I've been using Mendeley because after trying some pdf utils, it was the only decent way to mark (highlight) pdfs, and it's OOffice citation import plugin is nice, but it's been messing up my collections, and driving me nuts. 

Do any of these things mentioned allow highlighting of PDFs?

---

### Post by washakie on 2010-02-20
Just on Mendeley...

I use this a lot, and find it really helpful. Does anyone have experience with both Mendeley and Zotero that could argue for one or the other. I haven't quite found that Zotero fills the same purpose as Mendeley, but I may be missing a feature somehow??

I also note, that Mendeley has zotero synchronization it seems.

---

### Post by PraveenKvayalil on 2010-06-22
Please see this thread if you want to use EndNote in Linux.
[http://ubuntuforums.org/showthread.php?t=1504680&highlight=endnote]("http://ubuntuforums.org/showthread.php?t=1504680&highlight=endnote")

---

### Post by ugm6hr on 2010-06-22
> **washakie said:**
> Just on Mendeley...

I use this a lot, and find it really helpful. Does anyone have experience with both Mendeley and Zotero that could argue for one or the other. I haven't quite found that Zotero fills the same purpose as Mendeley, but I may be missing a feature somehow??

I also note, that Mendeley has zotero synchronization it seems.

Indeed - they are different in design.

I used to use Zotero, but it is better designed for tracking urls (e.g. for abstracts), whereas Mendeley is better at storing / storing full PDFs of documents.

You could use both, but I have found Zotero redundant now that I use Mendeley.

---

### Post by normandin on 2010-06-23
> **ugm6hr said:**
> Indeed - they are different in design.

I used to use Zotero, but it is better designed for tracking urls (e.g. for abstracts), whereas Mendeley is better at storing / storing full PDFs of documents.

You could use both, but I have found Zotero redundant now that I use Mendeley.

Agreed, Zotero and Mendeley appear to offer rather distinct functionality.  That being said, Mendeley can do continuous imports of your Zotero or CiteULike database (eee the "Zotero/CiteULike" tab in Mendeley preferences).  I've never used this feature myself, but friends mentioned that it's worked well for them.

---

