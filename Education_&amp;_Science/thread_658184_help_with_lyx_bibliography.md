---
title: "help with lyx bibliography"
date: 2008-01-04
forum: Education &amp; Science
---

### Post by iopo on 2008-01-04
Hi everybody,
I feel king of stupid: I have been trying for the last 5 days to insert a Bibtex bibliography in lyx!
Insert-List/TOC-Bibtex bibliography. Then "Bibtex generated bibliography" appears in brown at the bottom of the document. I can also insert citations, but when I generate the pdf (or the dvi, or the ps) I have question marks instead of the citations and no bibliography at the end of the document!
Is there something really simple I'm missing? Or there is some kind of magic I need to do?
Thanks a lot!

---

### Post by kleeman on 2008-01-04
I assume you have told the bibligraphy where to find the citations i.e. the location of the *.bib file. If so this problem may have something to do with the style you are using. Change this in Document--->Settings--->Document Class
and see whether you can get the refs to show up. I have found lyx a bit quirky in this area.

---

### Post by iopo on 2008-01-05
Hi Kleeman,
thanks for your reply. I tried what you suggested but it did not work: I tried to change from "article AMS" to "article" and "article (paper)" but I still have the same problem.
What is really killing me is the total absence of error messages. Can I generate a pdf from a lyx file using the terminal? Maybe I miss a package and I just don't know it!
Thanks!

---

### Post by kleeman on 2008-01-05
Attach your lyx and bib files and I'll have a look.

---

### Post by iopo on 2008-01-05
Hi Kleeman,
here are my two files. Anyway, I'm pretty sure its a bug in Lyx. I managed to make it work with exactly the same steps as above. The only difference is that I changed the directory of both the files or just the bib file. Basically, I copied both files in my home dir, on my desktop and in a folder on my desktop. Then I opened one copy of the lyx file at the time and added one of the three copy of the bib file. Total is 9 combinations. Sometimes it would work, sometimes not, sometimes it would add the bibliography at the end but the citations would be question marks and sometimes the citations would be there but no bibliography at the end. I could not figure out a pattern. Can you replicate it?
Thanks!

---

### Post by kleeman on 2008-01-05
I used lyx-1.5.3 and when I tried dvi I got the ? for the references but the bibliography appears OK. Then I tried pdf and it worked fine. Seems a bit flakey to me, as I said bibliography support in lyx can be a trial at times. What I would do would be to export to a latex file (pdflatex option) and then compile manually:

latex filename
bibtex filename
latex filename
latex filename

Then look and print the dvi file.

Not ideal but usually works and you can look at the output to see if you can spot where the error is coming from...

---

### Post by iopo on 2008-01-05
Hi Kleeman,
everything worked out great! The dvi is just perfect! Although there are several warning and error messages I guess they are not important. What matter is that it worked! 
Thanks again.

---

### Post by GSBoomer on 2008-01-16
Perhaps I've missed something, but the latest I see in the repository is 1.5.1. 

kleeman, how did you get 1.5.3 installed?

---

### Post by s57nev on 2008-01-17
I'd love to get 1.5.3 version on my system. Now I have 1.5.2 and writing my thesis with Lyx. Lyx is a wonderful tool for such texts. I can't imagine how could I work without it. Writng equations in Lyx is realy easy . Anyone here who have deb file for Gutsy and 1.5.3 ?? Thanks !

---

### Post by iopo on 2008-01-17
[https://launchpad.net/ubuntu/+source/lyx/1.5.3-1](https://launchpad.net/ubuntu/+source/lyx/1.5.3-1)
choose your buillds and click on "resulting binaries" on the left. 
I'm trying to install it now but there are a bunch of dependencies to satisfy. I'll let you know how it goes.
Best

edit: done! it's quite a headache but it is possible

---

### Post by kleeman on 2008-01-17
You can also build your own which is what I do:

1) Download the three source files from the last post (*.dsc, *.orig.tar.gz  and *.diff.gz). * here means the appropriate prefix for the file.

2) issue
dpkg-source -x *.dsc

3) change into the resulting subdirectory and issue

dpkg-buildpackage -rfakeroot

If you get a bunch of failed dependencies at this step then install the required packages.

There are two 1.5.3 amd64 debs here:
[http://www.math.nyu.edu/faculty/kleeman/amd64/](http://www.math.nyu.edu/faculty/kleeman/amd64/)

install with 

sudo dpkg -i lyx_1.5.3-1_amd64.deb lyx-common_1.5.3-1_all.deb

---

### Post by akniss on 2008-01-18
> **kleeman said:**
> You can also build your own which is what I do:
1) Download the three source files from the last post (*.dsc, *.orig.tar.gz  and *.diff.gz). * here means the appropriate prefix for the file.
2) issue
dpkg-source -x *.dsc


kleeman,
I followed these directions, and now have 2 .deb files (lyx_1.5.3-1_i386.deb and lyx-common_1.5.3-1_all.deb).  I've never built debs before so this may sound like a dumb question.  Would these be useful to others?  If I posted them, could someone else use them, or are they specific to my machine?   I'd be happy to post them for others to use if they would be valuable.
Thanks,
Andrew

---

### Post by kleeman on 2008-01-18
> **akniss said:**
> kleeman,
I followed these directions, and now have 2 .deb files (lyx_1.5.3-1_i386.deb and lyx-common_1.5.3-1_all.deb).  I've never built debs before so this may sound like a dumb question.  Would these be useful to others?  If I posted them, could someone else use them, or are they specific to my machine?   I'd be happy to post them for others to use if they would be valuable.
Thanks,
Andrew
Yes they may be. The ones I posted only work on 64bit versions of Ubuntu while yours work on 32bit versions.

---

### Post by akniss on 2008-01-19
> **kleeman said:**
> Yes they may be. The ones I posted only work on 64bit versions of Ubuntu while yours work on 32bit versions.

I have posted debs here:
[http://ubuntuforums.org/showthread.php?p=4169598#post4169598](http://ubuntuforums.org/showthread.php?p=4169598#post4169598)

---

### Post by Lukyan on 2009-04-07
Hi, is there a way to put the section Bibliography of LyX in the Table of Contents?

---

