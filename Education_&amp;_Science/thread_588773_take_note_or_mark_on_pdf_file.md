---
title: "take note or mark on pdf file"
date: 2007-10-23
forum: Education &amp; Science
---

### Post by tanyeun on 2007-10-23
Hi all, 
I used to read pdf file using adobe reader professional on windows

I am wondering is there any software that boost the same feature on Ubuntu

thx,

David

---

### Post by machoo02 on 2007-10-23
What about [PDFedit]("http://pdfedit.petricek.net/pdfedit.index_e")?  I haven't tried it yet, but I think it offers some of the functionality of Adobe Acrobat.  It's in the repositories for Gutsy.

---

### Post by harishg on 2007-10-23
Abiword can convert pdf files to html files as long as the document is pretty simple and does not include images or equations.

---

### Post by tanyeun on 2007-10-24
I failed to make PDFedit with error message:
........
reference to `textoutput::SimpleWordEngine::operator()()'
collect2: ld returned 1 exit status
make[2]: *** [pdfedit] Error 1
make[2]: Leaving directory `/usr/local/pdfedit-0.3.2/src/gui'
make[1]: *** [pdfedit] Error 2
make[1]: Leaving directory `/usr/local/pdfedit-0.3.2/src'
make: *** [src] Error 2

any suggestion? thx.

---

### Post by tweedledee on 2007-10-24
> **tanyeun said:**
> I failed to make PDFedit with error message:


You shouldn't need to build it.  It's in the repos for Gutsy, or you can download a package for Fiesty at [http://www.getdeb.net/](http://www.getdeb.net/) (just search for pdfedit).  It works fine for a few edits, but seems to take expontentially longer to deal with each sequential edit.  I've found if I have to make many changes/additions, saving after every 10 or so and closing/reopening keeps it from getting too slow.  PDFedit also doesn't support graphical changes yet.

Basically, if you just want to add a few lines of text or make small changes, I'd recommend PDFedit.  If you need to make a huge overhaul, Abiword is probably better.

---

### Post by tanyeun on 2007-10-25
thanks guys
I finally installed it successfully,

---

### Post by Lady Owl on 2008-02-20
> **machoo02 said:**
> What about [PDFedit]("http://pdfedit.petricek.net/pdfedit.index_e")?  I haven't tried it yet, but I think it offers some of the functionality of Adobe Acrobat. 


Hmmm... Doesn't look user-friendly at all. 

At work we have Windows, and there I was adviced to try PDFViewer, as we are not offered Adobe pro just for commenting etc. Only those that need more advanced features than that can get it. [SIZE="1"](It's so annoying - Adobe reader allows commenting, but only if the creator of the file has allowed it, and most of the files are probably created with programs not paying attention to that aspect at all, or then the creator has not payed attention...)[/SIZE]

---

### Post by ssam on 2008-02-21
xournal

---

### Post by tanyeun on 2008-03-04
WOW, that's a good one, 
but it is a little pity not be able to make bookmarks Orz

---

### Post by ItalOz on 2008-03-06
> **ssam said:**
> xournal

That's a beauty...!

---

### Post by rax_m on 2008-03-07
This  helped me lots! Thanks

---

### Post by emyline on 2010-12-12
hi everyone,
i installed xournal right now and i really like it. it's quite simple and very useful!

there is just one problem working with it:
after i marked some passages in the text, i tried to export the (marked!) file to .pdf
but the only thing i saw at the exported file were the marking colors but no text at all. 

so is the only chance to get my markings saved in saving the file as an .xoj ?!?

it's not a big problem at all, but i'm thinking about printing the coloured files with a microsoft computer (at work, for free :wink: ) sometimes.
so getting a "complete" exported .pdf will be quite useful for me someday...

does anyone has a solution for my gimcrack problem?

cheers,
emy

---

### Post by n3gbz on 2010-12-12
Great tool!  Exactly what I needed!

---

### Post by ugm6hr on 2010-12-14
> **emyline said:**
> it's not a big problem at all, but i'm thinking about printing the coloured files with a microsoft computer (at work, for free :wink: ) sometimes.
so getting a "complete" exported .pdf will be quite useful for me someday...


This should just work on v0.4.5
[http://xournal.sourceforge.net/manual.html#printing](http://xournal.sourceforge.net/manual.html#printing)

---

### Post by kaspar_silas on 2011-01-18
O have you checked out mendeley desktop? It's got a lovely user interface for editing and marking up pdfs.

Thou I haven't compared to xournal which judging by the comments I should.

---

### Post by tanyeun on 2011-02-01
looked back to the question I asked
I think so far xournal is my best choice
it's good enough for me to mark this thread SOLVED

it runs very fast under linux
and all I need is annotation and bookmark
before it doesn't have bookmark function
I wrote one last summer
patch can be found here
[http://sourceforge.net/tracker/?func=detail&aid=3151144&group_id=163434&atid=827735](http://sourceforge.net/tracker/?func=detail&aid=3151144&group_id=163434&atid=827735)

---

### Post by vikramsingh on 2012-08-24
xournal : Great tool man ):P

---

### Post by overdrank on 2012-08-24
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

