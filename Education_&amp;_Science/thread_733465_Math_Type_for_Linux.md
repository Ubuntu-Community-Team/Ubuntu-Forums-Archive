---
title: "Math Type for Linux?"
date: 2008-03-23
forum: Education &amp; Science
---

### Post by EcoDude on 2008-03-23
I'm on the verge of making the switch to Linux from Windows but have encountered a possible roadblock.

I use LaTeX on Windows (MikTeX + TexnicCenter) and use MathType to symbolically produce equations. MathType allows one to highlight and right click the equation, then paste the converted to LaTeX equation into any document. In other words, I can symbolically type out equations and then paste the resulting LaTeX code into my LaTeX IDE of choice because MathType converts the symbols into LaTeX code automatically.

I was wondering if there are any options in Ubuntu or Kubuntu that allows the symbolic creation of equations and then allows conversion into LaTeX.

Any help would be greatly appreciated! :)

---

### Post by smartboyathome on 2008-03-23
I think the OpenOffice Equation package may be what you are looking for. Check the repos for it. :)

---

### Post by EcoDude on 2008-03-23
Thanks for the help :)...but repos? 

I know that OOWriter exports to LaTex but I'm not sure that this would be a good solution.

---

### Post by thk on 2008-03-23
You need to check out LyX. Best writing tool I've come across. There is also a plugin for OOWriter which will allow you to type LaTeX equations and embed them into a document. Its not symbolic however. You have to type raw LaTeX. LyX does have a nice gui for entering equations.

---

### Post by akimatsu123 on 2008-03-26
He's not asking for a latex writer. 

He's asking for a software that converts symbolically typed math into latex code. Mathtype is a great software, and i use it too. 

I could not find any good replacements on ubuntu. and you wouldnt want to learn all the keyboard shortcuts all over again anw. the best solution i found was to install Wine (a program that lets u run simple windows programs on linux) and just install mathtype on wine. you get the exact same interface. everything is the same, besides the fact that you can't insert equations into MS word.

to install wine, just 

sudo apt-get install wine

---

### Post by EcoDude on 2008-03-26
Actually, I think I may have answered my own question, although I cannot verify at this time because I'm using various Live CD versions of various Linux Distributions...just to be sure Ubuntu is the best :)

KOffice has a component called KWord which apparently has a built in formula editor called KFormula which will allow symbolic expression of formulas and then convert these to LaTeX. The KFormula website is here:

[http://www.koffice.org/kformula/](http://www.koffice.org/kformula/)

If anyone can verify my claim, I would greatly appreciate it. 

Thanks to akimatsu123 for understanding exactly what I'm looking for. I assume that under Wine I simply install that application, run Math Type in that window, and then cut and paste into my LaTeX IDE. Correct?

Again, thanks for the help and I'd appreciate any verification of the KFormula LaTeX export. :KS

---

### Post by akimatsu123 on 2008-03-27
yes. after you install wine, navigate to the install .exe file, right click, and select run with wine windows emulator. it will install the program just like it is in windows. you cna open the program by going under applications --> wine --> programs.

---

### Post by Claus7 on 2008-05-19
> **akimatsu123 said:**
> everything is the same, besides the fact that you can't insert equations into MS word.

Very bad indeed... And not only in word, but also in power poing as well...

---

### Post by gatorbrit on 2008-05-29
> **akimatsu123 said:**
> He's not asking for a latex writer. 

Hthe best solution i found was to install Wine (a program that lets u run simple windows programs on linux) and just install mathtype on wine. 


Follow on question - how do you create/edit a mathtype equation in open office writer in Ubuntu?


Thanks

---

### Post by Vivaldi Gloria on 2008-06-11
Am I understanding this correctly? 

Mathtype has some menus of symbols etc. and then you drag the ones you want with mouse to form a formula and then mathtype converts them to latex code and you copy that latex code and paste it in a latex document? 

This must be the the worst and slowest way of writing latex. The whole point of latex is to get rid of making formulas by hand and you make formulas by hand in order to use them in latex? 

What am I missing here?

---

### Post by gatorbrit on 2008-06-11
You are correct - but I people I collaborate with don't use latex - math type is used by them and so I need to use a common platform.

---

### Post by Vivaldi Gloria on 2008-06-11
> **gatorbrit said:**
> You are correct - but I people I collaborate with don't use latex - math type is used by them and so I need to use a common platform.

OK. I see.

---

### Post by gatorbrit on 2008-06-11
Actually, this is the key issue.  If I worked on my own I would never touch windows, but being able to share documents and spreadsheets with non-linux users is an essential part of my work.  I am sure that this is a common issue.  However, I think the way OO is moving, soon this will not be a problem.

---

### Post by RVDowning on 2008-06-18
Have you been able to get the integration and summation symbols to appear correctly when using Mathtype in Wine on Linux? 

There seems to be something messed up with the fonts.  If I create a MathType document with the messed up symbols using Wine in Linux and then transfer it to a Windows system they display correctly.

---

### Post by gatorbrit on 2008-06-18
I can get mathtype to work OK and I think the fonts are OK - but the issue is still that copying a mathtype equation into a document is a hassle.  

In windows I can open mathtype, type and equation and then just copy it straight into word.  But when I do this in linux using wine for both mathtype and word, word crashes.  

I tried copy the equations from mathtype to OO writer, but they wouldn't copy - its as if you can't copy from a wine loaded app to a native linux app.

You can save the mathtype formulas as image files and then import them, but this adds at least a few extra steps.

I should say that I did get  mathtype to work better by installing it in its own wine folder.  I followed these instructions - this might help you with the fonts.

Cheers

Rich

---

### Post by eldragon on 2008-06-18
im not going to be of much help with this post, but, can i ask why?

i personally found it quite useful not having to use an equation editor in order to enter math formula into latex.

i just find doing $\left({ /frac{this}{that} }\right)_{some_under}^{some_above}$ quite faster than using an editor. thats the main reason i use latex :D

its quite tedious at first, when you are not used to it, but once it grows on you, its as fast as typing :D

---

### Post by gatorbrit on 2008-06-18
> **eldragon said:**
> im not going to be of much help with this post, but, can i ask why?

i personally found it quite useful not having to use an equation editor in order to enter math formula into latex.

i just find doing $\left({ /frac{this}{that} }\right)_{some_under}^{some_above}$ quite faster than using an editor. thats the main reason i use latex :D

its quite tedious at first, when you are not used to it, but once it grows on you, its as fast as typing :D

You are correct - LaTex is the choice for equation typesetting.  I don't use it but I am familiar with it.  My problem is that I am in academia and my coauthors use word, and only word.  I love linux and really want to adapt to it, but I am always constrained by having to have compatability with people I work with.

So for now, I have to figure out an alternative - and mathtype might be it.

---

### Post by eldragon on 2008-06-18
> **gatorbrit said:**
> You are correct - LaTex is the choice for equation typesetting.  I don't use it but I am familiar with it.  My problem is that I am in academia and my coauthors use word, and only word.  I love linux and really want to adapt to it, but I am always constrained by having to have compatability with people I work with.

So for now, I have to figure out an alternative - and mathtype might be it.

there was a plugin for pidgin that would paste small images with latex formulas. you could adapt that :D

---

### Post by lad.kocb on 2008-06-23
"texmacs" might be an answer to your needs.

I have installed texmacs on everything, even on windows. Texmacs
is a very good tool for many purposes, but I have used it mostly
as - indeed - replacement of MathType. The only extra step is 
that you need to save the equations by "exporting to latex", 
and as in using MathType, you need to edit or copy also a little   
set of macros.

My students most often use "kile" and "texmacs" in parallel. 
"kile" provides a fast way to insert macros for equations, 
sections, chapters, even the codes of symbols, while 
"texmacs" is most useful when designing more 
complex mathematical structures.

It takes a little practice to get accustomed to texmacs, it is
a sort of "emacs", so it is not only GUI. For example, you can 
enter the subscript mode by typing underline, the same for superscripts. 

I have not yet upgraded, but a little search on the web shows 
that "texmacs" is easily installed on 8.04.

---

### Post by lad.kocb on 2008-06-23
Vivaldi Gloria has written in Reply 10
QUOTE START
[I]Am I understanding this correctly?
Mathtype has some menus of symbols etc. and then you drag the ones 
you want with mouse to form a formula and then mathtype converts 
them to latex code and you copy that latex code and paste it in 
a latex document?
This must be the the worst and slowest way of writing latex. The whole 
point of latex is to get rid of making formulas by hand and you make 
formulas by hand in order to use them in latex?

What am I missing here?[/I]
QUOTE END

The short answer is "You are missing a lot".
Now to the longer answer. The whole point of latex is definitely not
to get rid of making formulas by hand. When D. Knuth started TEX, there
even was not much GUI around. The whole point of TEX is typesetting
of mathematics represented by rather simple commands and macros in
plain text files, editable in any text editor. TEX then produces DVI files 
and there is a whole set of different additional programs to take advantage 
of the DeVice Independent binary representations. PDFTEX and PDFLATEX produce
directly PDF, avoiding the DVI step.

You are right, the simple math can easily be entered straight into the text,
but try entering a continuous fraction with terms containing fractions and 
braces etc. In such situations the graphical interface is very helpful.
I have been using tex and latex for nearly 20 years, and for longer math 
I still prefer using texmacs (LYX is a bit too "independent"), on MSwindows 
(fortunately less and less often) I still use an ancient version of 
Scientific Word written for windows 3.1, for more complex structures.
(expensive, but very good MSwindows scientific workplaces still available 
at [http://www.mackichan.com/]("http://www.mackichan.com/") )

On texmacs I wrote another comment in this thread.

One more note for those who still need to use MSwindows: an alternative to 
"paid for" MathType is  TexAide which Design Science gives away for free. 
TexAide is a stripped down version of MathType, only the TEX representation 
is contained. ( [http://www.dessci.com/en/products/texaide/]("http://www.dessci.com/en/products/texaide/") )

---

### Post by lad.kocb on 2008-06-23
I am sorry, this is a third entry today. I remembered one more
nice software piece:

See the downloadable applet DragMath
[http://www.dragmath.bham.ac.uk/]("http://www.dragmath.bham.ac.uk/")
where you get MathType functionality inside any web browser with java.
As DragMath is open-source, you are free to download and re-distribute.
DragMath requires Java 1.4.2 or later

---

### Post by Vivaldi Gloria on 2008-06-23
I don't want to hijack this thread but with apologies to OP I have to answer lad.kocb.

> When D. Knuth started TEX, there even was not much GUI around. 

And practice has shown that LaTeX is still better than all gui editors. 

> You are right, the simple math can easily be entered straight into the text, but try entering a continuous fraction with terms containing fractions and braces etc.

Are you kiddin me? Of course it is easier with LaTeX.

Pal, you need to read more about logical vs. visual design. Visual design may be OK for a short paper. But it is no good for complex documents.

You should read sections 1.4-1.5 in Lamport's book - LaTeX, A Document Preparation system. There he compares the two approaches and gives an example (about the inner product) which shows it's much efficient to use LaTeX.

Suppose I wrote a paper in LaTeX and sent it to the journal A using their style file. Now A rejected the paper and I want to send it to the  journal B. But B uses a completely different syle & layout. What am I to do? Simple, I download their style file and use it. I don't have to change anything in the document. The whole document gets typeset automatically to the new style!!

And that is the main point of LaTeX - you don't bother with the page format and appearance of the document which makes you loose time, makes the document rigid, and afterall humans are not very good at it. LaTeX takes care of all visual design of the document so you just type the content, and believe me, typing is much faster than typing plus visual design. Get a complex document with a lot of formulas and have it typed by two people - a Word wizard and a LaTeX wizard. The LaTeX guy will write it in a fraction of the time it takes the word guy to write it. 

How many times did you strugle with word when it puts an item in an odd place, or it starts numbering things which are not supposed to be numbered, and so on. I go mad even if I try to write a two page document with word. Writing a 100 page scientific document with word? - Better kill me so the pain & suffering ends.

And I stress the fact that humans (and Word) are not good at designing complex documents. The primary strength of LaTeX is its typesetting quality. I can always tell which hw is written using LaTeX and which is not. The ones written with LaTeX look great and the others look like sh*t.

Also read:

[http://nitens.org/taraborelli/latex](http://nitens.org/taraborelli/latex)

[http://www.ecn.wfu.edu/~cottrell/wp.html](http://www.ecn.wfu.edu/~cottrell/wp.html)

[http://www.andy-roberts.net/misc/latex/latexvsword.html](http://www.andy-roberts.net/misc/latex/latexvsword.html)

---

### Post by lad.kocb on 2008-06-23
Neither I want to monopolize this thread, but the last entry
by Vivaldi Gloria calls for a little comment. Yes, I completely
agree with you! Except of your language in the last sentence 
I could have written  exactly what you have written. 
I was not talking about Word or any other word processor. 
I was talking exclusively about TeX/LaTeX.
Even the "Scientific Word" is latex based, it has nothing to do 
with "the other" Word from Redmond.

I was simply saying that when you are going to design a 
complicated structure in TEX, it might be helpful to use 
a graphical tool. I also said that I have been using latex for
nearly 20 years (and I hope to do it for the rest of my 
scientific carrier - which unfortunately is much less
than 20 years).

I have no doubts that latex is THE best way now available 
(and in foreseeable future) to work with mathematical texts. 
All computer algebra systems I know about export latex, preprint 
archives are based on latex, most physics journals I know accept
latex submissions, etc. Just to finish, I am afraid that the
younger generation is getting sometimes too microsoftized, as 
well as some "less theoretical" fields of science, who are 
unfortunately falling deeper and deeper in Microsoft web of 
tricks and lies.

So dear Vivaldi Gloria, continue your fight! Good luck! But 
please, do not waste your ammunition on me. I am on your side.

---

### Post by Vivaldi Gloria on 2008-06-23
I am not fighting or carrying around "ammunition" but I guess I got carried away there a bit. Well, nice that we agree. Sorry if I sounded harsh.

---

### Post by hx129 on 2008-08-03
I agree with lad.kocb. Latex is nice in formatting maths, not typing maths. A few examples shows that: a fraction takes "\frac{}{}" 9 key strokes to complete in latex, but just "^C F" 3 key strokes to complete in Mathtype. A large bracelet takes "\left( \right)" 13 key strokes to complete in latex, but "^C (" 3 key strokes to complete in Mathtype. Typing a matrix reads as "\begin{array}...\end{array}" in latex. And "^M 3" gives you a 3x3 matrix in mathtype.
Therefore, if you work as a teaching assistant and have tons of equations to type for the class everyday, type all latex code by hand is definitely going to kill you.

Now, speaking of workaround. At first I thought there is a workaround in latex: define Macros. But after defining macros on macros on macros, the readability of latex code degrades a lot. Especially when you are working with some one else(coauthor a paper, working with an instructor), don't expect everyone to understand your macros. 

For the questions in this thread, I would recommend to install vmware , run mathtype on it, and connect to it via rdesktop. It's far more reliable than wine. You don't have any of the fonts isuses.

---

### Post by KatBuntu on 2008-08-04
You can use texmacs [http://texmacs.org]("http://texmacs.org")
Simple and proffessional

---

### Post by Vivaldi Gloria on 2008-08-04
> **hx129 said:**
> I agree with lad.kocb. Latex is nice in formatting maths, not typing maths. A few examples shows that: a fraction takes "\frac{}{}" 9 key strokes to complete in latex, but just "^C F" 3 key strokes to complete in Mathtype. A large bracelet takes "\left( \right)" 13 key strokes to complete in latex, but "^C (" 3 key strokes to complete in Mathtype. Typing a matrix reads as "\begin{array}...\end{array}" in latex. And "^M 3" gives you a 3x3 matrix in mathtype.
Therefore, if you work as a teaching assistant and have tons of equations to type for the class everyday, type all latex code by hand is definitely going to kill you.

Good. You go in to matrix mode 2 seconds faster in mathtype. But you'll loose that 2 seconds when you are actually making that matrix. Do we have to go over this again? Take any technical book and have it written by a latex guru and mathtype guru. Latex guru will finish it much faster. 

What part of this do you not understand? People can type much faster than they compose formulas by hand! 

Let me repeat it for you:

People can type much faster than they compose formulas by hand! 

You don't know what you are talking about.

Latex is THE choice for technical documents all around the world for a reason. The first of them being that it's a lot faster. This is not the only reason. Read my above post to grasp some of the other reasons.

> **hx129 said:**
> Now, speaking of workaround. At first I thought there is a workaround in latex: define Macros. But after defining macros on macros on macros, the readability of latex code degrades a lot. Especially when you are working with some one else(coauthor a paper, working with an instructor), don't expect everyone to understand your macros. 

There is no need for a workaround because latex is FASTER! Gee.

If you want to use macros in latex then use descriptive names and you'll remember them. Also put them in a separate file if there are a lot of them, else put them in the preamble.

> **hx129 said:**
>  For the questions in this thread, I would recommend to install vmware , run mathtype on it, and connect to it via rdesktop. It's far more reliable than wine. You don't have any of the fonts isuses.

Yes, the OP has a valid reason not to use latex, so this may be a valid suggestion. But I suggest wine if mathtype works with it. Wine is close to native, requires less resources, it's foss, and you don't need to buy windows to use programs with it.

---

### Post by tehwizardd on 2012-09-21
Anyone know if there is mathtype like math editor for linux that allows to handwrite equations with mouse and convert those into images or text?

---

### Post by lisati on 2012-09-21
> **tehwizardd said:**
> Anyone know if there is mathtype like math editor for linux that allows to handwrite equations with mouse and convert those into images or text?

A lot can change in four years. 

From the forum code of conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

