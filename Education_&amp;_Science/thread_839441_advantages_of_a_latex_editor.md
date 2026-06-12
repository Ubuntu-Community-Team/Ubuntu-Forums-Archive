---
title: "advantages of a latex editor"
date: 2008-06-24
forum: Education &amp; Science
---

### Post by ZeldaFan on 2008-06-24
What are the advantages of a latex editor as opposed to using microsoft word/equation editor? I know it makes you documents more professional looking, but does it have the same capabilities, if not more, as equation editor when it comes to inserting equations/mathematical information in my papers. And how does it handle inserting data tables/charts/images? Finally, when people say a latex editor makes a document more professional, can it format a document in a variety of publishing styles, such as ACS, MLA, etc? Or is it restricted to just one particular layout?

---

### Post by hugmenot on 2008-06-24
Yes to all questions, but not necessarily the editor itself does that.

A LaTeX editor it tries to assist you in as much as you need to memorize less commands. Say you want to insert the symbol &#966; into an equation, in Word and in the Latex editor you can click the &#966; button, but if you know the command is \phi you can simply enter it and continue typing without taking your hands off the keyboard.
The same is true for more complex constructs. The Latex editor will for instance assist you in adding figures by inserting all the boilerplate markup text necessary for this. But in principle you could do away with a special Latex editor and use a simple plain text editor.

This would be the instruction to insert a graphic into a floated figure, i.e., it would be placed with some whitespace in the corner of a page, independent of the surrounding text, like e.g. in a journal.
```
\begin{figure}
	\centering
	\includegraphics{image.jpeg}
	\caption{An example figure}
	\label{fig:the-example}
\end{figure}
```


The crucial difference between Word and Latex is that TeX, the actual engine, devotes a lot more thought on how the elements in your document will be layouted. This additional computation goes from small scale things, like how high to place numerator in a fraction and calculate its surrounding spacing, to large scale things, like how it distributes words into lines and paragraphs, how much text to fit on a page, where to dynamically float the figures so that a typographically optimal page layout is achieved.
In Word things have to be reasonably quick, because the image of the page is calculated and refreshed after every keystroke. So it compromises on a lot of quality aspects. In Latex this is not necessary because the real typesetting is only done when the user thinks it is time to check the final output.

Latex has a lot more advantages for scientific writing. It handles cross-references, citations and bibliographies, TOCs, tables and figures and more in a clean, explicit, and consistent manner. Not necessarily without some effort (you have to learn how to do it), but a lot less pain once you master it.

There are a multitude of templates for all fields and styles, in addition to many packages that do some very specific small things. One can get lost in this wealth of information in the beginning, but TeX is more than 30 years old and many people have used and contributed to it.

---

### Post by rajan on 2008-06-25
also latex can be used to create web pages and presentations. you want to use latex2pdf for creating a thesis or paper, latex2pdf (using the beamer class) again for presentations, and latex2html for html content. those are the actual commands and if you have them installed, they'll read any .tex file and make it look really good at the end. 

presentations look really good in latex's beamer class and they're really customizable. there's really no comparison between latex's equations and anything on MS. 

there's even a way to write music on latex. what i'm trying to say is that you can essentially use latex as your default starting point, no matter what you're producing in the end. hope this helps.

---

### Post by hugmenot on 2008-06-25
Err, no. [Wrong]("http://packages.ubuntu.com/search?mode=filename&suite=gutsy&section=all&arch=i386&searchon=contents&keywords=latex2pdf")

---

### Post by rajan on 2008-06-25
> **hugmenot said:**
> Err, no. [Wrong]("http://packages.ubuntu.com/search?mode=filename&suite=gutsy&section=all&arch=i386&searchon=contents&keywords=latex2pdf")


wow what a childish reply. a simple correction saying "no it's actually pdflatex and not latex2pdf" would have shown people how intelligent you are, and not how much you have to learn.

---

### Post by rhm on 2008-06-26
LaTeX handles very large files (think dissertations) much better than MS Word. Try inserting a couple of pages worth of equations or images in Word and you will notice a significant reduction in performance and very likely end up crashing it once it becomes too large. Since LaTeX is text based, it takes almost no toll on your system while you are writing. Also, large files can be broken down into smaller files and input into a main file.

As far as graphics go, LaTeX will place the images where you tell it to, unlike MS Word, which has the nasty habit of moving your images around at its convenience. Also, LaTex's ability to set vector graphics in the document lets you keep high quality graphics at any resolution or scale, given that your original image is of high enough quality; however, MS Word will reduce the quality of most images you paste into a document or scale inside a document.

Finally, many publishing entities have developed their style sheets which will format your document to their liking as long as you follow certain rules while creating it. That way you can have several different output formats for a document with minimal effort.

---

### Post by hugmenot on 2008-06-26
> **rajan said:**
> wow what a childish reply. a simple correction saying "no it's actually pdflatex and not latex2pdf" would have shown people how intelligent you are, and not how much you have to learn.

Please don&#8217;t make a fuss about this petitesse. I&#8217;m short in indulgence because the level of noise on this forum is so unbelievably high. Nothing personal. okay?

---

### Post by ZeldaFan on 2008-06-26
Thanks everyone for all the replies. They were certainly helpful as I think I will invest some time in learning latex. I was just wondering, what latex editor do you guys recommend or currently use?

---

### Post by meborc on 2008-06-26
> **ZeldaFan said:**
> Thanks everyone for all the replies. They were certainly helpful as I think I will invest some time in learning latex. I was just wondering, what latex editor do you guys recommend or currently use?

a friend of mine is writing he's master thesis all in latex... engineering stuff, so a lot of diagrams and formulas

he is using texmaker (in repos), which is quite good

---

### Post by ahmatti on 2008-06-26
> **ZeldaFan said:**
> Thanks everyone for all the replies. They were certainly helpful as I think I will invest some time in learning latex. I was just wondering, what latex editor do you guys recommend or currently use?

I use Emacs with auctex, which gives you a nice preview. If you don't like emacs then I recommend using Kile.

---

### Post by akniss on 2008-06-26
Some useful discussion on this topic in this thread:
[http://ubuntuforums.org/showthread.php?t=98120](http://ubuntuforums.org/showthread.php?t=98120)

---

### Post by math_x3 on 2008-06-26
By the way, you can practice editing mathematical latex equations online using:
 [_Online Latex Equation Editor_]("http://www.numberempire.com/texequationeditor/equationeditor.php").

---

### Post by rajan on 2008-06-27
> **ahmatti said:**
> I use Emacs with auctex


second that. emacs is really nice with latex.

---

### Post by luisito on 2008-06-28
Emacs is good, but it is also very hard to use at the beginning. You will save a lot of frustration using kile.

---

### Post by ppm on 2008-06-29
Here
emacs + preview-latex

[http://www.gnu.org/software/auctex/preview-latex.html](http://www.gnu.org/software/auctex/preview-latex.html)

sudo apt-get install preview-latex-style

---

### Post by RebounD11 on 2008-06-29
I like LyX a lot... look nice and it's pretty easy to use :D

---

### Post by Chessmaster on 2008-07-01
> **RebounD11 said:**
> I like LyX a lot... look nice and it's pretty easy to use :D

I just started using Lyx myself. Still new at it, so too early to evaluate from my perspective - but it looks quite good.

How have other people found it? Or is using LaTex itself better. (I am using it for writing academic papers).

---

### Post by Buzzdee on 2008-07-01
I would definitely recommend Kile, since (as in Texmaker) you can assign Keystroke bindings, eg make an equation code with ctrl+e giving
\begin{equation}

\end{equation}
and bringing your cursor between the two lines. The advantage of Kile over Texmaker is that you can assign a binding to \text{} (what you can't do in Texmaker, afaik) which you need a lot in formulae. According to the Green Book (some sort of scientific typesetting bible) you need to write subscripts like normal text and variables italic. Otherwise, if you have the inlet of a reactor and call it Q_{in), the "in" will be italic, takes as variables i and n, correctly it should be Q_{\text{in}}, done with two clicks in my case (ctrl+d for subscript, ctrl+\ for text and done). 

Coming back to the topic, I think that's the real advantage of using a dedicated editor, you don't need to remember code AND you don't need to leave your keyboard, providing a very good workflow.

Best regards, 
Bastian

---

### Post by brunovecchi on 2008-07-01
I think it's not a good idea to start from scratch to both Emacs and LaTeX. Something more beginner-friendly would be LyX, or plain LaTeX on a text editor with some support, like Kile or Gedit. Gedit has a LaTeX plugin that works great (you have to activate it through preferences).

---

### Post by eldragon on 2008-07-01
considering the fact that writing equations as text is MUCH faster than actually pointing and clicking buttons....thats one of the biggest advantages of using latex for math formulas. But you will need a semester to get used to it :D

editing, i just use vim / gedit or whatever editor. i like vim better.

once you got used to the latex way, there is no turning back.

1) all other documents look awful in comparison

2) its actually faster to produce a finished paper.

---

### Post by hugmenot on 2008-07-01
If you don&#8217;t know emacs, and being a Word user I can assume you don&#8217;t, refrain from starting out with Emacs. You would have to battle on two fronts concurrently. Taming the beast of Emacs and tamign LaTeX. So I agree with the previous two posters.

---

### Post by ZeldaFan on 2008-07-02
Ok so I think I've narrowed it down to either lyx or kile. I think I'm going to go with kile.

---

### Post by gatorbrit on 2008-07-04
One thing that is overlooked in the discussion of LaTex and word (or OO office) WSYWIG editors, is that making a perfectly formatted document is often not important in academia.  This is because when I submit a paper to an academic journal, they are going to reformat it anyway using their own type setting method.

I'm not trying to stir up trouble, I'd just be interested on folks opinions on this - if the final format of your document is publication, then does it matter that much how the document is made?  Does it matter that the superscript is perfectly place in a formula etc...

---

### Post by Buzzdee on 2008-07-04
No, it doesn't. Either, your text gets reformatted or you get a template (in Word format) in which you need to write, together with some minor formatting directions. Then the paper is check-read by the publisher and formatting errors are improved.

---

### Post by Buzzdee on 2008-07-04
> **ZeldaFan said:**
> Ok so I think I've narrowed it down to either lyx or kile. I think I'm going to go with kile.

I would suggest you try both - they're both installed perfectly with Synaptic and are very alike. Just write one text in one editor and one in the other and see which one fits you best.

---

### Post by hugmenot on 2008-07-04
> **gatorbrit said:**
> One thing that is overlooked in the discussion of LaTex and word (or OO office) WSYWIG editors, is that making a perfectly formatted document is often not important in academia.  This is because when I submit a paper to an academic journal, they are going to reformat it anyway using their own type setting method.

I'm not trying to stir up trouble, I'd just be interested on folks opinions on this - if the final format of your document is publication, then does it matter that much how the document is made?  Does it matter that the superscript is perfectly place in a formula etc...

Sure, but how much of your writing goes into submission to a journal? If you're a student, then most likely none of it. As a student you&#8217;re forced to be a one man publishing house. And if you started LaTeX as a student, you might want to continue using the better mode of entry and assistive features of LaTeX/BibTeX even for submission material. Either you export to doc, if the editor requires you to, or they accept .tex as submission format (many do).
Looking at how in the recent decades the tasks of a scientist have shifted to comprise anything related to the publishing but the final layout, it seems likely that also more of typesetting will soon belong to it. I mean some journal even require you to have proper Word cross-references in your documents from footnote marker to footnote, from citation to reference, etc. They have stringent requirements wrt. graphic formats, and whatnot.
In the past in labs you had a dedicated photographer/dark room technician, a technical illustrator to draw your plots on millimeter-paper, a typist to transfer your manuscript to typewritten text, a statistician, etc. Nowadays as a scientist you have to do all these yourself with software solutions

---

### Post by DrOlaf on 2008-07-04
> **gatorbrit said:**
> One thing that is overlooked in the discussion of LaTex and word (or OO office) WSYWIG editors, is that making a perfectly formatted document is often not important in academia.  This is because when I submit a paper to an academic journal, they are going to reformat it anyway using their own type setting method.

I'm not trying to stir up trouble, I'd just be interested on folks opinions on this - if the final format of your document is publication, then does it matter that much how the document is made?  Does it matter that the superscript is perfectly place in a formula etc...

Sadly, that is true for me as well, although I think it varies from discipline to discipline. In my field (life sciences) most journals do just want doc format, but the situation may be different if you are a physicist or a mathematician.

---

### Post by samden on 2008-12-09
I find everyone wants .doc format too. But the vast majority of stuff I write is minor documents for internal use - and LaTeX is great for them. I am currently writing my thesis, and LaTeX is ideal - word processors just die on documents that large. Having switched to LaTeX last year I now find I virtually never open a word processor, when I do it is usually to open .doc files someone has emailed me. I now use plain text and LaTeX. LaTeX is just a simpler and more reliable way of writing stuff, once you are used to it. The getting used to it bit is the issue.

I have used Texmaker for a while, but am just switching over to gedit with the LaTeX plugin as I never use all the fancy features of Texmaker anyway so this suits me better.

---

