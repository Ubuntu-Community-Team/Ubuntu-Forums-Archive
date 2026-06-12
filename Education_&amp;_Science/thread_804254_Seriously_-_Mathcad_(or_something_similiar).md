---
title: "Seriously - Mathcad (or something similiar?)"
date: 2008-05-22
forum: Education &amp; Science
---

### Post by Gripp on 2008-05-22
I am a structural engineer.  among my duties is the mass production of calculations for various items.  often these are the almost the same from one job to the next (one beam is 30' long with 500plf, the next 25 with 700... same calc, just change the variables)

where i can i create a mathcad report that i simply change a few variables at the top of the program and print the calcs...

but i have found this near impossible with linux...

while i could use a spreadsheet application, that isn't 'presentable' material (i need to show the calculations themselves, the assumptions being made, etc.)

does anyone know of a program, or mixture of programs, that i can use in linux to accomplish this?  i would love if it were some add on to latex that allows for the creation of fields and then the subsequent recalculation of the following formulas...

---

### Post by CRISM on 2008-05-23
I too am an engineer and like to use MathCad. I've been using linux (Ubuntu) for about 6 months, so can't claim to be anything like an expert. But so far I've been unable to find anything similar to MathCad. The closest I've come (in math functionality) is the Python software. It's a very powerful programming language with lots of modules available to download for graphing, special calculations, and all sorts of tasks. But it requires that you write a program to accomplish what you want to do. Not much like MathCad I'm afraid, and it certainly doesn't provide the documentation aspects of MathCad. I too wish I could find something like it.

---

### Post by thisismalhotra on 2008-05-23
Well I dont know what your guys needs are, but please look at octave it is a free clone/similar of matlab and shoudl work for you guys..

---

### Post by Gripp on 2008-05-23
it just doesn't seem like it should be that difficult to me.  (then again i dont program!)  just make some CAS integratable with a word processor (oOO or latex..) in the same way other OLE's work... but then again each object would have to recognize those previous to it, so maybe not too simple...

the best idea that i have come up so far is to just create a database with a GUI and have it generate the formatted report... something like enercalc
but that is far more painful than mathcad... 

and i haven't used matlab for a few years, but last i knew it didn't work great with formating (pretty formulas and the likes)
has this changed?

---

### Post by ptcbus on 2008-05-24
There is a program called Scilab and is very similar to Matlab (I do not know about mathcad) . And you can write very very short scripts (which are quite intuitive) in Scilab to calculate stuff with different numbers for variables. 

To install scilab you can either use the termninal: sudo apt-get install scilab

or else use the synaptic package manager and search for scilab.

---

### Post by sam_delta on 2008-05-24
check out [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)
windows-linux parallel programs

from link above:

matlab:

1) Matlab. [FTP] [http://www.mathworks.com/products/matlab/requirements.shtml](http://www.mathworks.com/products/matlab/requirements.shtml)
2) Octave. (+ Gnuplot) [http://www.octave.org/](http://www.octave.org/)
3) Scilab. [http://www-rocq.inria.fr/scilab/](http://www-rocq.inria.fr/scilab/)
4) R. 
5) Yorick. [http://wuarchive.wustl.edu/languages/yorick/doc/](http://wuarchive.wustl.edu/languages/yorick/doc/)
6) rlab.
7) Yacas. [http://www.xs4all.nl/~apinkus/](http://www.xs4all.nl/~apinkus/)
8) Euler. [http://euler.sf.net/](http://euler.sf.net/)

note , i have not tryied any of them, so i cannot recommend you any of them, i just copied the informatioin from the link stated at the beggining of my post

sam

---

### Post by meborc on 2008-05-24
you guys are missing the point... scilab is good... octave is good... maxima is good...

the question was about mathcad - a GRAPHICAL mathematics program, where you actually SEE the calculations in a very nice graphical way :)

being an engineer myself, i have not found anything to replace mathcad... but i hated it anyway, as it was so picky about how i should insert stuff 

i guess the best way is to have 2 things: scilab (matlab lookalike... make all calculations there... preserve the .sci files and change the values to get the answers) and latex editor... again preserve the file and change only the numbers/answers

i know it is stupid way of doing things, but it is the best way to do it for now

---

### Post by brunovecchi on 2008-05-27
I sympathize with the OP here... I got spoiled by MathCad (never used Matlab, I'm a molecular biologist so I wouldn't need it) and unfortunately I haven't found a replacement. The workflow with Mathcad is quite intuitive, you start writing text, then you insert a floating equation/function/graph, then you define and call variables on the fly while typing... Even if you are not writing a document this ability to mix equations and text comes quite handy in medium size projects, where comments aside formulas become really valuable  . Specially if you open the file a couple of months later.

---

### Post by dvase on 2008-05-28
I haven't actually used MathCad myself, however some of the functionality you describe, the ability to do calculations and plot within descriptive text, can somewhat be fullfilled by [Sage]("http://www.sagemath.org/").  Although more akin to Mathematica then MathCad, using the "Edit" tab within a worksheet allows the user to add descriptive text in between equations that can be LaTeX typeset.

---

### Post by TokyoYank on 2008-05-28
It's true, there are no easy math programs for Linux.  For those reading who have not used MathCAD, it seems reasonable to suggest Octave / etc.. but that suggestion is misplaced, because MathCAD to Matlab is apples to oranges.  

MathCAD serves and important function in math(s) education, encouraging students to focus on the equations and concepts instead of being side-tracked by C syntax.  The amount of "non math / computer" that the user must utilize is similar to the MS equation editor.  Results and answers are refreshed on the fly.  

.. As a result, it's often *very useful* in fields where the same / similar lengthy calculation must be repeated 2-3 times a week (but fully scripting a computer program takes more time than it's worth), such as engineering, chemical synthesis buffer calcualtions, etc..

In response to the OP, if a GUI similar to MathCAD were to be developed (to be placed on top of Octave, perhaps), it would likely have to be spearheaded by a education-minded group.  Many of the people reading this thread are actively engaged in research, and often times in that case, educating others is a distraction and black hole for free time. 

How many edUbuntu readers are out there?  From the edubuntu main site there does not appear to be a dedicated edubuntu forum..

---

### Post by tedrick65 on 2008-05-30
TokyoYank is spot on.

I'm a structural engineer that needs true documentation of what I did.  The equations need to be clearly visible and "live", not just symbolic.  They also need to print on paper (or pdf) just like they would if I was doing hand calcs.

Right now, there are two products for doing that...MathCAD and TEDDS.

Something like TEDDS may be more realistic for what the OP is looking for.  It runs both standalone and on top of MS Word.  Something similar on top of Oo would be a godsend.

---

### Post by Gripp on 2008-05-30
meborc - agreed, i hate it's pickyness with variables too... but it is the only prog of its kind. (unfortunately)

the need is for reports.  reports that will be read by non technical folk and that i will reproduce over and over again.

imagine you have 20 variables, and 20 pages of formulas.  pretty, formatted formulas, with text and the works.  professional. 

not really something that will algebraically solve 3 line laplace transforms... just something to plug and chug for me 

MathCAD simply lets you create a template document that you can change your variables each time you need to run a report. (just the **one** report.. and no need for dataentry/storage, so NO suggestions to use access please..)

this could be done with Writer and Fields, but that gets a bit complicated when your formulas start being based on logical statements and looking up databases (like member sizes and correlating area/modulus/inertia/etc.)

MathCAD works this all out nicely...  but it wont even work with Wine, much less has a linux replacement...

---

### Post by Gripp on 2008-05-30
> **tedrick65 said:**
> ... Something similar on top of Oo would be a godsend.

Amen

and thanks, i haven't heard of TEDDS before.  running to look that one up now.

---

### Post by TokyoYank on 2008-05-30
> **tedrick65 said:**
> ...  Something similar on top of Oo would be a godsend.
I also agree.   

Anyone know a clever way to get edubuntu developers to start working on a MathCAD-like intuitive GUI for Oo Calc / Spreadsheet?  Is there a edubuntu-related bug/request center?

---

### Post by vaccaromg on 2008-05-31
You might want to try out Sage ([http://www.sagemath.org/](http://www.sagemath.org/)) as a surrogate for Mathcad.  It has a notebook feature that reminds me a lot of a Mathcad worksheet.

---

### Post by Gripp on 2008-05-31
> **TokyoYank said:**
> I also agree.   

Anyone know a clever way to get edubuntu developers to start working on a MathCAD-like intuitive GUI for Oo Calc / Spreadsheet?  Is there a edubuntu-related bug/request center?

that is kind of my goal here.  I've seen posts like this from years back though, so I'm not keeping my hopes up...

and i have been spending some time trying to learn oOO macros and forms well enough to make something like TEDDS for a little while now.. I finally broke down and asked my Qs over at the oOO support forum and they basically told me to just use access........
if i could just take the things i know about word, and then those about writter and combine them i would be able to do it... just cant seem to get those overlapping deatures down in one or the other.

---

### Post by Gripp on 2008-05-31
> **vaccaromg said:**
> You might want to try out Sage ([http://www.sagemath.org/](http://www.sagemath.org/)) as a surrogate for Mathcad.  It has a notebook feature that reminds me a lot of a Mathcad worksheet.

thanks.  i've messed with sage briefly when I first got on ubuntu. my aim is to not show anything resembling computer coding - just formatter forulas like you might write by hand.

---

### Post by TokyoYank on 2008-06-01
> **vaccaromg said:**
> ...([http://www.sagemath.org/](http://www.sagemath.org/)) ... It has a notebook feature that reminds me a lot of a Mathcad worksheet.

Looking at screen shots [http://www.sagemath.org/screen_shots/misc/](http://www.sagemath.org/screen_shots/misc/)  I have some positive and negative reactions to it, in the context of the discussion in this thread:

[LIST]
[*]Good Point:  The show function presents nice-looking equations
[*]Not clear from screenshots/ unknown:[LIST]
[*]There is no "print view format", for example a format that strips out all show statements & plots onto one page
[*]Not so clear if it's possible and/or easy to click on an earlier entry on a saved notebook to change an early variable, and then have all fllowing lines update on the fly
[/LIST]
[*]Bad Point:  user must learn Python like interface
[/LIST]
Seems the best / unique aspect of MathCAD is that it goes backwards from most math programs:  instead of starting with the code and then presenting a nice looking *& human readable* equation, it uses the user's equation as the starting point.  

Gripp, if you ever make a list of people willing to help on the Oo project (despite not being a conventional programmer--I do mainframe number crunching written in Fortan77) please put my name down

---

### Post by Victormd on 2008-06-15
I'm a Civil Engineer and used Mathcad during my entire Ph.D. and simply loved it... I've also used octave, but as I read earlier and quote, "I was spoiled by mathcad." It's just too intuitive and extremely powerful! If anyone ever comes across anything like it for ubuntu, PLEASE, let me know! :)

---

### Post by omorr on 2008-06-15
I am a Mathcad user for almost 20 years. Questions like: Mathcad clone, replacement for Mathcad, Mathcad for Linux - has been posted many times on different forums and places. I can say that a Linux clone for Mathcad does not exist. I think that there is no interest or enough motivation in making one. On the other hand, Mathcad developers, unfortunatelly, did not make any significant improvements in last 10 years. 

I am using it on a daily basis (an older version). It drives me crasy sometimes and I am also searching a FLOSS replacement for it. The tipical answer one can find for this is: Octave, Scilab, SciPy,  Rlab, etc..(Matlab like software) or Maxima, Axiom, Yorick, Yacas (Computer Algebra Systems like Mathematica or Maple) or Sage (notebook oriented based on Python like language). I tried almost all of them but I think they are not suitable to the Mathcad users. 

My favorite at the moment is EuMathT (former Euler)[URL="http://mathsrv.ku-eichstaett.de/MGF/homes/grothmann/euler/"]
http://mathsrv.ku-eichstaett.de/MGF/homes/grothmann/euler/[/URL]
Although it is arround for almost 20 years it is not so wellknown. I am surprised because it is quite good and powerful considering that is a one-man project. The new version 5.x improved a lot and I could recomend it to a Mathcad user although is more similar to Matlab. Besides the numerical and plotting capabilities, it has Maxima and yacas backend for symbolic computations. In my oppinion it is the easyest of all to use and learn.

Just give it a try, see its demos and notebooks. It is a Windows software but I am using it on Ubuntu 8.04 under wine also with no problem.

---

### Post by ahmatti on 2008-07-03
> **Gripp said:**
> 
I am a structural engineer. among my duties is the mass production of calculations for various items. often these are the almost the same from one job to the next (one beam is 30' long with 500plf, the next 25 with 700... same calc, just change the variables)

where i can i create a mathcad report that i simply change a few variables at the top of the program and print the calcs...

but i have found this near impossible with linux...

while i could use a spreadsheet application, that isn't 'presentable' material (i need to show the calculations themselves, the assumptions being made, etc.)

does anyone know of a program, or mixture of programs, that i can use in linux to accomplish this?  i would love if it were some add on to latex that allows for the creation of fields and then the subsequent recalculation of the following formulas...

What about using Maple [http://www.maplesoft.com/?](http://www.maplesoft.com/?) It has a Linux version that works nicely in Hardy, I use Maple 11. Unfortunately it is proprietary, but at least you get rid of Windows! Maple basically has all the features the original post requested and you can also do calculations with units. I don't know how good it is as compared to Mathcad, since I have very little experience from Mathcad... 

Another commercial option is Mathematica [http://www.wolfram.com/](http://www.wolfram.com/), which I've never used. 

For Latex plugins you can look for various literate programming options. I use R+Sweave ([http://www.statistik.lmu.de/~leisch/Sweave/](http://www.statistik.lmu.de/~leisch/Sweave/)) myself for automatic report generation, the math is not symbolic, but I guess you could use it to parse equations into latex format. At least updating the calculations and plots is very simple, but the computations are displayed as R code by default..

---

### Post by sg007 on 2008-09-10
Hi, probably would be supportive for you a very simply package - CalcTeX. CalcTeX based on TeX or LaTeX input file with defined actions and basied on python gives a TeX or LaTeX file with calculated values. You need python and TeX compiler. For more info pls visite web page [http://sg.bzip.pl/CalcTeX/](http://sg.bzip.pl/CalcTeX/). There is a presentation in English version as well as sources of this presentation and all CalcTeX sources. Additionaly is avilable more advanced document but in Polish version but this document could be supportive due to couples of examples.
Let me know if you have any comments or questions.
I'm author of this package.

---

### Post by pipplum on 2008-09-27
Take a look at TEDDS from CSC 

[http://www.cscworld.com/tedds/](http://www.cscworld.com/tedds/)

It has a library of structural calculations and you can also create your own.

---

### Post by LaserJock on 2008-09-28
Regarding Edubuntu, there are really no resources (that is people) to work on software from scratch. There are only a handful (like 2-3) of people working on Edubuntu period so most focus has been on getting the distro together.

That said, I think the idea of a mathcad clone for Linux sounds very interesting. I've been in university science programs for the last 10 years and never used Mathcad but I just had a quick look at their website and the concept is intriguing. I've really not seen anything like it.

I think if people want to push this idea more there are a few things that would be helpful. 

First, just saying "we want a Mathcad clone" is probably not going to get anywhere. Mathcad is a large, established commercial program. It would take years to clone it. What you want to do, in my opinion anyway, is establish a specific, minimal set of tasks you want to be able to do. 

Second, from the list of tasks create a specification that ties them all together and puts some details down on paper as to what elements are needed, how they'll fit together, what parts already exist, and what's left to do. You should create some mockups and use-cases to help "sell" the project and to make sure people know what your trying to accomplish.

Thirds, I'd advertise the need for some young computer science majors who need a project along with some "old hats" who can mentor the process.

Fourth ....

Fifth, Profit :)

-LaserJock

---

### Post by ad_267 on 2008-09-28
There isn't really anything like Mathcad for Linux as people have said, but I think for the original posters needs a simple python script using Scipy and outputting LaTeX could easily meet the requirements.

Apparently some versions of Mathcad work well in Wine but I haven't tried this myself. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=263](http://appdb.winehq.org/objectManager.php?sClass=application&iId=263)

Oh and by the way sg007, I get a 403 Forbidden trying to access your website.

---

### Post by sg007 on 2008-09-28
> **ad_267 said:**
> There isn't really anything like Mathcad for Linux as people have said, but I think for the original posters needs a simple python script using Scipy and outputting LaTeX could easily meet the requirements.

Apparently some versions of Mathcad work well in Wine but I haven't tried this myself. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=263](http://appdb.winehq.org/objectManager.php?sClass=application&iId=263)

Oh and by the way sg007, I get a 403 Forbidden trying to access your website.

Thank you ad_267 for finding a error on my page.

Generally, I agree that MathCAD is a unique program as well have not any 100% equiv program on linux. On linux we have many programs which allows more advanced calculation but do not gives a well-looks documents, at least in easy way. Due this fact CalcTeX is a program focusing on giving a 'well-looks document' with calculation, 'well-looks' becouse besed on (La)TeX standards. Probablly I title bite exaggerate if I say that CalcTeX is an alternative for MathCAD on linux but CalcTeX is still under constuction... and who knows...:)

BTW I am aware of CalcTeX limits and I know that CalcTeX use could be a problem for people without (La)TeX experience but I still sustain my prevouise opinion that CalcTeX could be supportive in this case. 

Additionaly on the CalcTeX web page are included examples:
[http://sg.bzip.pl/CalcTeX/examples/comb-temp-ch4-en.pdf](http://sg.bzip.pl/CalcTeX/examples/comb-temp-ch4-en.pdf) and *.tgz 
[http://sg.bzip.pl/CalcTeX/examples/bh-en.pdf](http://sg.bzip.pl/CalcTeX/examples/bh-en.pdf)
This examples could be supportive for better CalcTeX understanding, at least I hope. Regards, sg007

---

### Post by TokyoYank on 2008-10-01
> **LaserJock said:**
> I think if people want to push this idea more there are a few things that would be helpful. 

First, just saying "we want a Mathcad clone" is probably not going to get anywhere. Mathcad is a large, established commercial program. It would take years to clone it. What you want to do, in my opinion anyway, is establish a specific, minimal set of tasks you want to be able to do. 

Second, from the list of tasks create a specification that ties them all together and puts some details down on paper as to what elements are needed, how they'll fit together, what parts already exist, and what's left to do. You should create some mockups and use-cases to help "sell" the project and to make sure people know what your trying to accomplish.

Thirds, I'd advertise the need for some young computer science majors who need a project along with some "old hats" who can mentor the process.
Thanks!  Very helpful post.  I think a lot of us who are enthused to help simply don't know where to start ... Meaning, the second step in listed above will be a significant hurdle.

But, first things first.


==> If you're reading, it means you want something like MathCAD.  Tell us what that means--**what do you want the software to do?**  What are the essential features you're looking for?  

.. As for me, I want 1) on-the-fly updating of algebra type equations *that I typed in using an equation editor  2) symbolic algebra "solve for X"


PS Yay Southpark reference.  :D But if no underpants are involved in the plan, I don't see how profit could be a realistic expectation :)

---

### Post by xadder on 2008-10-01
Nobody has mentioned texmacs yet. Combined with Maxima it seems to offer nice printable equations and solutions, with good LaTeX output. I have played a little with and still have mixed feelings though - some things work really well, but then I get "stuck" in various ways. Some of this is undoubtably my inexperience with both texmacs and Maxima. It would be interesting to hear of other experiences, and if this helps for a mathcad-type search.

---

### Post by jpkotta on 2008-10-10
It really sounds like Mathematica can do what you want.  It is completely cross-platform; it has nicely typeset formulas; it can integrate text, calculations, and plots; and can print nice postscript documents (that can be converted to PDFs with ps2pdf).  It's proprietary and expensive, but so is MathCAD.

---

### Post by brunovecchi on 2008-10-10
> **jpkotta said:**
> It really sounds like Mathematica can do what you want.  It is completely cross-platform; it has nicely typeset formulas; it can integrate text, calculations, and plots; and can print nice postscript documents (that can be converted to PDFs with ps2pdf).  It's proprietary and expensive, but so is MathCAD.

No offense, but obviously you haven't tried MathCAD. Mathematica doesn't cut it.

---

### Post by TokyoYank on 2008-10-11
Can't blame people for not reading the middle posts.  But I still think this thread could be useful to gauge what are the most important features we want to see.

I'll go through an old post or two to tweeze out the feature requests.
> **Gripp said:**
> meborc - agreed, i hate it's pickyness with variables too... but it is the only prog of its kind. (unfortunately)

the need is for reports.  reports that will be read by non technical folk and that i will reproduce over and over again.

imagine you have 20 variables, and 20 pages of formulas.  pretty, formatted formulas, with text and the works.  professional. 

not really something that will algebraically solve 3 line laplace transforms... just something to plug and chug for me 

MathCAD simply lets you create a template document that you can change your variables each time you need to run a report. (just the **one** report.. and no need for dataentry/storage, so NO suggestions to use access please..)

this could be done with Writer and Fields, but that gets a bit complicated when your formulas start being based on logical statements and looking up databases (like member sizes and correlating area/modulus/inertia/etc.)

MathCAD works this all out nicely...  but it wont even work with Wine, much less has a linux replacement...
Gripp, if you're reading, please feel free to correct the order of importance of feature requests:[LIST=1]
[*]Re-evaluation of a long sequence of equations using shared variables, after changing one or two of the initial conditions
[*]Cross-reference access to a pre-defined database or library (units)
[*]Preserve formatting / priority on quality of printed work
[/LIST]Anything I missed?


Anyone need math higher than symbolic algebra??

---

### Post by khmorse76 on 2008-11-16
As a communting CivE student, I'd love to have a MathCAD variant for linux.  I hate being tied to the school's computer labs.  BTW, thanks for pointing out the other apps that could get me what I need in the short term.

---

### Post by fr@nk on 2009-01-22
I found something similar to MathCad(not so powefull but free), it's SMath:
[http://en.smath.info/forum/default.aspx?g=posts&t=73](http://en.smath.info/forum/default.aspx?g=posts&t=73)
It's required Mono 2.0, witch I compiled from source and all works fine (in 8.10) and in Ubuntu 9.04 it's only required to install some pakages from Synaptic package Manager:
mono-common
mono-jit
libmono-winforms2.0-cil

---

### Post by Endolith on 2009-01-23
I haven't used MathCAD, but wxMaxima might do what you want?  It does worksheets of symbolic algebra, where you can change initial conditions and recalculate the worksheet, and has the capability to use units, though you might have to jump through some hoops for that.

I don't know of a way to make it do things like [this]("http://www.hrs.co.nz/dynimages/mv13-Mathcad_style.jpg"), though, with the permanent display of the output arranged on a page.  Latex/texmacs might be able to  do that?  Maybe you should post a screenshot of the functionality you need.

> Using OpenOffice as the front end of Maxima or Scilab, Octave, etc is the great idea that I have been also thinking. 
 
I have also tried TeXmacs + Maxima and Lyx + Maxima. The first pair works great under Linux but only quite slow under windows. Also, learning texmacs drives me crazy. It is quite different from what I get used to (such as Lyx or Word). It also still need some work.  - [related thread]("http://www.oooforum.org/forum/viewtopic.phtml?t=52544")

Can't you just run MathCAD in Wine, though?

---

### Post by TokyoYank on 2009-01-24
Endolith,

thanks for the link to the OOffice forum thread.  The project mentioned therein is appropriate:

[http://comppad.sourceforge.net/](http://comppad.sourceforge.net/)


The author might use some help.  I hope JAVA programmers reading might take a peek at his script.



And yes, MathCAD really is different.  
(The post by Muddybeemer on March 18 2007 on the above OO forum thread post eloquently states the situation.)

---

### Post by jpkotta on 2009-01-25
> **brunovecchi said:**
> No offense, but obviously you haven't tried MathCAD. Mathematica doesn't cut it.

You're essentially right.  I've used MathCAD a total of about an hour.  

What is it about MathCAD that makes it so much better?  Is it because MathCAD is "automatically pretty"?  I've seen pretty, usable documents done with Mathematica, but it takes a bit of effort.

---

### Post by muddybeemer on 2009-01-29
Hello,

I'm the "developer" for CompPad, the OpenOffice extension TokyoYank mentioned above.  I noticed a spike in downloads on Sourceforge, went looking for the source, and found this thread.

This is a very interesting thread, and highlights some of the reasons why I started working on CompPad.  I am trained as a mechanical engineer but have done a lot of programming in VB, Fortran and Python.  So I'm one of a small group of people who can appreciate MathCad and also write some code.  I'm using CompPad as an excuse to learn Java, as well as possibly develop a useful application.  

MathCad is a very unique program, and I don't think most "computer people" really understand it, and for good reason.  After all, the shell-based applications like Matlab, octave, Python with the Scipy libraries, etc.. are much more powerful, and are not that hard to use if you have that inclination.  I do a lot of work with these tools.  

There are two areas where MathCad sets itself apart for me: Units of measure, and presentation of results. 

Units of Measure:  Mathcad automatically handles units within the calculations, and if you make an error in your math and don't get the right units, you will find that error much sooner with MathCad.  This is actually my first priority right now for CompPad.

Presentation:  Your boss, co-worker or customer is short on time and less computer-literate, and doesn't want to read code to understand your calculation - they want to look at mathematical expressions in a format they understand, mixed in with illuminating plots or other media.  They want to tweak a number and instantly see a result, in the same way you can change a spreadsheet cell and see how it affects the calculation.  No other applications do that effectively.


The reason I chose to work on an OpenOffice extension is that OpenOffice already has a nice equation editor, and it has the framework for embedding other objects such as plots or images.  And the API is powerful and well-documented.  And the resulting documents should be accessible by anyone with OpenOffice.

I think an open-source equivalent to MathCad can eventually come about, but it will have to become clearly viable before it will attract a pool of developers.  

I realize the experimental demo I released isn't anywhere near usable, but I would be interested to hear people's comments on the general concept.  I would like to focus my work in a direction that will make it useful to some small group of people as soon as possible, initially only to myself perhaps, but then maybe as a tool for education.

Wow, that's a long post.  If you read it all, I thank you.

---

### Post by bjtaylor01 on 2009-02-04
Not sure if anyone has mentioned SAGE yet on this thread. Quick background on me I have a lot of experience with Matlab, Octave, Maple, Mathcad, etc.. so for all you Mathcad users out there switching to Ubuntu/linux I know what you are going through.

That said Mathcad is great because you can print off your work and show it to someone and they can follow your math very easily. SAGE also pretty prints all of your work in an easy to read format. You can try it for free online without installing anything on your computer just through the web at:
[http://www.sagenb.org/login](http://www.sagenb.org/login), just sign up for a free account and give it a try, or see what other people have done.

Or you can download it: [http://www.sagemath.org/](http://www.sagemath.org/)

Sage is probably closer to Maple to Mathcad, but if you do some research on the background of this SUPER math program I think you will see the potential that I did. 

For Mathcad units and flexibility I have just installed it on a Virtualbox machine, but I think with some effort you could develop the notebook portion being used by SAGE to allow you to move equations freely around on the page. +Spent hours with WINE and no luck, so I would not recommend that route yet with MATHCAD.

Good luck,
-Ben

---

### Post by Endolith on 2009-02-19
> **TokyoYank said:**
> The project mentioned therein is appropriate:

[http://comppad.sourceforge.net/](http://comppad.sourceforge.net/)

And yes, MathCAD really is different.  

So it seems like the only real competitors mentioned so far are CompPad and SMath?

> **muddybeemer said:**
> MathCad is a very unique program, and I don't think most "computer people" really understand it

Yeah, I haven't used MathCad before, but it looks like a really useful program for electrical engineering, so now I'm looking into all these alternatives.

> **muddybeemer said:**
> Units of Measure:  Mathcad automatically handles units within the calculations, and if you make an error in your math and don't get the right units, you will find that error much sooner with MathCad.  This is actually my first priority right now for CompPad.

Does CompPad handle units?  The [GNU units program]("http://www.gnu.org/software/units/") has a huge library of units it can convert, though some of the unit names are unwieldy and it can only do simple math:

> [FONT=Courier New]> units -1v "3 kilometers + 500 feet" yards
    3 kilometers + 500 feet = 3447.5066 yards

> units -1v "one hundred V / 5 ohms" A
    one hundred V / 5 ohms = 20 A

> units -1v "1/(2*pi*sqrt(10*microF*100 mH))" Hz # [resonance frequency of an LC circuit]("http://en.wikipedia.org/wiki/LC_circuit#Resonance_effect")
    1/(2*pi*sqrt(10*microF*100 mH)) = 159.15494 Hz

> units -1v "sqrt(mu0/epsilon0)" ohm # [impedance of free space]("http://en.wikipedia.org/wiki/Impedance_of_free_space")
    sqrt(mu0/epsilon0) = 376.73031 ohm

> units -1v "sqrt(4 k stdtemp 1 kohm (20 kHz - 20 Hz))" nanovolt # [URL="http://en.wikipedia.org/wiki/Thermal_noise#Noise_voltage_and_power"]thermal noise of a resistor
[/URL]    sqrt(4 k stdtemp 1 kohm (20 kHz - 20 Hz)) = 548.99727 nanovolt[/FONT]     It seems like something that might work as a backend?  And there is [a version for Windows]("http://gnuwin32.sourceforge.net/packages/units.htm").

> **muddybeemer said:**
> And the resulting documents should be accessible by anyone with OpenOffice.

That's a huge benefit, I think, but all the macros would have to be included along with the document, no?  It's not really an OpenOffice extension; it's an OpenOffice document with macros in it?

> **bjtaylor01 said:**
> Not sure if anyone has mentioned SAGE yet on this thread. 

It's kind of minor, but the one problem I have with Sage is that I can't define custom infix operators.  I use "x||y" in electronics a lot to mean "(x*y)/(y+x)", and in Sage I guess my only option is to make it a par(x,y) function instead.  Not quite as readable.  Currently I use wxMaxima for this stuff, but it's not actually very easy to go back and change values and re-execute the worksheet.  I really like the idea of creating a single worksheet (with embedded schematic and graphs) that I can re-use for different problems.

> SAGE also pretty prints all of your work in an easy to read format.wxMaxima also pretty prints the equations and has inline graphs and such.

> You can try it for free online without installing anything on your computer just through the web at:
[http://www.sagenb.org/login](http://www.sagenb.org/login), just sign up for a free account and give it a try, or see what other people have done.Except that the site is always down.  :)

---

### Post by dmitrijledkov on 2009-02-23
Try TeXmacs

1) Graphical 
2) Beautiful formulas (LaTeX THE best math formulas you ever going to see)
3) Plugin interface to SAGE

Total

Configurable, simply to change some values and print!

---

### Post by sf-andrew on 2009-04-18
> **Endolith said:**
> So it seems like the only real competitors mentioned so far are CompPad and SMath?



There is also TEDDS, another closed source package for mostly civil/structural engineering that is integrated with MSWord - [http://www.cscworld.com/tedds/](http://www.cscworld.com/tedds/)

---

### Post by sdbrogan on 2009-04-30
Ahmati mentioned literate programming with LaTex/Sweave/R, & several people have suggested Maxima; perhaps you might look at the maxima-emacs package for literate programming with LaTex/EMaxima/Maxima.  From a LaTeX document within Emacs you can write code for Maxima & have the Maxima output displayed as LaTeX.  Also, does anyone know a similar method for literate programming with Octave, preferably through Emacs ?

---

### Post by parhyang on 2009-06-03
look like similiar concept to Mathcad are:
[SMath]("http://en.smath.info/") Studio + mono
[CompPad]("http://comppad.sourceforge.net/") (i recommended since its powerfull) .. but still in alpha version

of course u can do it using OpenOffice.org WRITER with built in function, probably using Table reff like this. [pdf]("http://syont.files.wordpress.com/2007/10/ooorg-writer-lembar-kerja-otomatis.pdf") & [pdf]("http://syont.files.wordpress.com/2007/10/contoh-lmbrkrj-dgn-ooo-writer.pdf")
.
[IMG]http://syont.files.wordpress.com/2007/10/textcalculationooowriter.PNG[/IMG]
.
In my opinions, the dissadvatages are branching/conditional statement and iteration, arithmetic and values being used. If it's your goals set, you can build with Python(TM). here's an examples  ([pdf]("http://syont.files.wordpress.com/2009/05/glassboxdi_v02_print.pdf")) about design module of RC Beams design, singly and doubly. Plain text output but readable.

---

### Post by kordenal on 2010-03-11
Hello guys.
Can anybody help me with some bear question:
is it possible to re-calculate all Maxima's formulas in TexMacs document after file opening ?

Best regards.

---

### Post by Endolith on 2010-03-11
I don't know.  It's possible in WxMaxima, though.

---

### Post by kordenal on 2010-03-11
> **Endolith said:**
> I don't know.  It's possible in WxMaxima, though.

You're right. wxMaxima can do it. 
But I need TexMacs to create some text with mathematical formulas and inclusions of Maxima's calculations.
After changes of some parameters it's need to recalculate all Maxima's formulas to perform new result.
How to do it most quickly?

---

### Post by meng1usa on 2010-09-21
I been tried SMath Studio, it's a recently started project, and seems not get too much attention and support.
It actually is the clone of mathcad, but certainly not as functional as mathcad.

take a look
[http://en.smath.info/forum/default.aspx?g=posts&t=561](http://en.smath.info/forum/default.aspx?g=posts&t=561)

---

### Post by agestrada on 2010-09-23
Currently using Mathcad 6.0 on ubuntu 10.4 with Wine without problems. I have to try all the functionality but so far is good.

EDIT: Save option doesn't work. Big issue. I'm using it with VMWare.

---

### Post by radioboy on 2010-10-08
What about SageTeX?
[http://www.sagemath.org/doc/tutorial/sagetex.html]("http://www.sagemath.org/doc/tutorial/sagetex.html")
One can include visible and silent blocks of Sage code, generate plots, etc.
The Sage documentation suggests a special configuration, but it's not difficult to do (I did it today, indeed):
[http://www.sagemath.org/doc/installation/sagetex.html]("http://www.sagemath.org/doc/installation/sagetex.html")
Since Sage accepts Python code, I suppose it wouldn't be difficult to call long procedures using "execfile()".

---

### Post by BFris on 2011-03-18
Yeah, I know it's an old thread. Seriously, CompPad is the closest thing you're gonna find. It's an OpenOffice/ LibreOffice extension.

Seriously. It rocks. Like MathCAD, you get pretty equations in natural math format. And you get units! Once you get used to calculating with units, it's hard to using anything else. Oh yeah, and graphs, too. Though I'm a little unclear at how extensive the graphs are. Not sure if anything beyond  xy scatter plots are available yet.

It's still rough around the edges, but very usable.

Where it beats MathCAD are that the equations are OpenOffice Formulas. So they're publication quality. As are the graphs.

---

### Post by Mariotte on 2011-04-20
Hello, everybody.
This is my first post here, I hope I have a good start...

Did you have a look at Smath Studio?
[http://en.smath.info/forum/default.aspx?g=posts&t=561](http://en.smath.info/forum/default.aspx?g=posts&t=561)
You will need mono to make it run.

As a Mathcad user, I was looking for something similar; it is something more than that.

I hope this helps.

Mario

---

### Post by davost on 2011-07-12
Check out the [Reinterac]("http://www.reinteract.org/trac/")t program. It is a really neatly implemented package for worksheets with live python  calculations mixed in with text, live plots and graphics. 

Python is of course powerful enough and the logic for reevaluation worksheets sean to work flawlessly. Check out the [screencast]("http://people.gnome.org/%7Eotaylor/reinteract-demo.html"). For the purposes of documenting engineering calculations the only missing thing is mathematical type setting :(

---

### Post by jaredssix on 2011-07-27
Have you guys seen [CompPad]("http://extensions.services.openoffice.org/en/project/CompPad")? It performs exactly like MathCAD, prints and simultaneously solves formulae in OpenOffice, handles units, etc. 

Functionality is limited--no IF statements, no SOLVE functionality . . . but it's well on its way!

---

### Post by gunksta on 2011-07-28
Why would you want a tool that restricts you to a single language?

I strongly recommend [org-mode]("http://orgmode.org/"), which is a major mode of the one and only Emacs text editor. More specifically, you want to look at [babel]("http://orgmode.org/worg/org-contrib/babel/"), which is a built in system within org-mode that will let you do just about anything you are clever enough to make it do.

Using babel and org-mode it is possible to built a printable/publishable file which contains all of your code embedded in the original PLAIN TEXT file. Sweave is nice, but only works with R. There is something similar to Sweave that works with Python but I don't remember what it is called. With org-mode, I can mix and match AND use org-mode to pass data from one programming language to another.

So, I could write a web-scraper in python and pass the scraped numbers off to R or I could be a masochist and run the numbers in a custom lisp function. Of course, that would involve me being able to do more than hack at lisp, but I could do it if I really wanted to.

Different languages have different strengths. Depending on how you plan to publish the results, org-mode gives you the ability to embed latex and html directly into the file, so you can control the output, input equations, etc.

The learning curve is steep. The system is so flexible it is sometimes a little frightening, but once you figure it out, you'll wonder why more people don't use it.

Added bonus - it is being actively developed by a large and energetic community.

---

### Post by fransfrans on 2011-07-29
has anyone tried Miramath?

---

