---
title: "Math Expression Editor"
date: 2009-07-13
forum: Education &amp; Science
---

### Post by mintygood on 2009-07-13
Hey all,
Just wanted to know if you guys knew of a math expression editor that I could use to take notes on and do homework.  In short, I just want a program that is similar to a text editor that will allow me to input complex calculus and trig problems in addition to misc graphs and text so I can print it out and hand it in or stick it in my binder.  Thanks!

---

### Post by hubie on 2009-07-13
You might find [this thread]("http://ubuntuforums.org/showthread.php?t=1145200") informative.

---

### Post by samden on 2009-07-13
To be honest, for taking those sorts of notes fast you're probably better with a pen and paper in my opinion. Sure we want to do everything with the computer, but sometimes the simplest technology is the best! :-)

For typing up mathematical formula, go for LaTeX - text-based, fast once you get the hang of it, should be exactly what you are looking for. Very high quality results.

I'd just prefer to have a pen and paper in class than be stuck because I can't quite remember the code off the top of my head to get that little detail of my equation right...

---

### Post by XCan on 2009-07-14
Absolutely latex. I've been using to take notes for quite some time. It's very fast once you learn the commands and the typeset text is actually typographically correct by default and very beautiful. However, if you run into big matrices, you're screwed, but that goes for all the so called math apps, only difference is that the other math apps suck as regular expressions as well.

---

### Post by mintygood on 2009-07-16
I've tried LyX but wasn't very impressed.  I found it extremely awkward moving from normal typing to mathematical expressions.  It seemed like I had to take my hand off the keyboard and click "math" every time I wanted to string in an equation.  Also, I could not figure out how to make additional paragraph breaks.  It was only allowing me to go down the the line directly below the previous paragraph which made my notes look chaotic.  I guess I'll have to try LaTeX out.

---

### Post by meho_r on 2009-07-16
LyX is just a very friendly "frontend" for LaTeX. There are shortcuts for almost everything, but you'll have to read a little :P And it has very good documentation.

If you want to use "plain" LaTeX, then try with Kile which is the best LaTeX editor. Texmaker is very good too. And there are gedit + LaTeX plugin and Vim + LaTeX addon...

EDIT: BTW, LaTeX isn't "piece of cake", you'll have to take time to get used to it. E.g., there is nothing like two spaces or two empty lines between paragraphs made by Space of Enter keys in LaTeX. If you want additional horizontal space, there is \hspace{} command, and for vertical space, there is \vspace{} command (inside {} you put an amount, e.g., 1cm). But reward for patience is that you'll always produce docs of highest quality (don't even try to compare with OpenOffice, MS Office etc.)

---

### Post by InfernalNeutrino on 2009-07-16
I agree with the general sentiment on Latex. There was one student in my quantum class who took notes with Kile, and at the end of the day had better (and more complete) notes than I did with pen + paper. Of course, he was very good at it, so I wouldn't expect to be able to pull that off to begin with :) . If you put in the time though, it'll pay off in a big way. Cheers!

---

### Post by Chronon on 2009-07-18
> **meho_r said:**
> LyX is just a very friendly "frontend" for LaTeX. 
EDIT: BTW, LaTeX isn't "piece of cake", you'll have to take time to get used to it. E.g., there is nothing like two spaces or two empty lines between paragraphs made by Space of Enter keys in LaTeX. If you want additional horizontal space, there is \hspace{} command, and for vertical space, there is \vspace{} command (inside {} you put an amount, e.g., 1cm). But reward for patience is that you'll always produce docs of highest quality (don't even try to compare with OpenOffice, MS Office etc.)

That's not entirely true.  latex will interpret a blank line as a new paragraph. IMO, you shouldn't be fiddling about with micro-formatting your document anyway, especially when taking notes.

You can also enter a "verbatim" environment if you need to carefully format your text in a specific way.

---

### Post by XCan on 2009-07-19
> **Chronon said:**
> That's not entirely true.  latex will interpret a blank line as a new paragraph. IMO, you shouldn't be fiddling about with micro-formatting your document anyway, especially when taking notes.

You can also enter a "verbatim" environment if you need to carefully format your text in a specific way.

Agreed, these easy-to access micro-formatting possibilities in softwares like Word is what makes the end document look like crap, together with the fact that of course the default templates are crap as well, breaking all typographical rules. 

For example, in Latex, a regular question posed by a new user is how to make the lines wider. However, there is a very good reason why the default template's lines are narrow.

---

### Post by ahmatti on 2009-07-19
Texmacs is also an option: [http://www.texmacs.org/](http://www.texmacs.org/). Although personally I prefer Latex (with Emacs + auctex).

---

### Post by wanichan on 2009-07-19
Assuming it's not too technical, or you don't have a reviewer who is anal about formatting, you could probably get by with open office .org math which is kinda like word's equation editor, if a little trickier to use but much easier than latex.

---

### Post by ahmatti on 2009-07-20
Come to think of it you might also want to try Sage [www.sagemath.org](www.sagemath.org), it gives you a notebook interface where you can use latex and write the calculations as well as create graphics from data and plot functions. You can try it and look at published examples here: [http://www.sagenb.org/](http://www.sagenb.org/). 

These will give you an idea of Sage's capabilities:
[http://www.sagenb.org/home/pub/354/](http://www.sagenb.org/home/pub/354/)
[http://www.sagenb.org/home/pub/566/](http://www.sagenb.org/home/pub/566/)

Note as I stated in my previous post I use Latex myself, but Sage is an interesting option that I'm considering to learn. If I want to embed some calculations to my documents I use Sweave [http://www.stat.uni-muenchen.de/~leisch/Sweave/](http://www.stat.uni-muenchen.de/~leisch/Sweave/)

I'm in teaching myself so I use it to write course material rather than handing in exercises, but I sure would be glad if the students handed in the reports written in something Latex based with decent graphics rather than MSword with excel graphs...

---

### Post by cb951303 on 2009-07-20
My only advice to you is STAY AWAY from openoffice math.

---

### Post by XCan on 2009-07-20
> **ahmatti said:**
> Come to think of it you might also want to try Sage [www.sagemath.org](www.sagemath.org), it gives you a notebook interface where you can use latex and write the calculations as well as create graphics from data and plot functions. You can try it and look at published examples here: [http://www.sagenb.org/](http://www.sagenb.org/). 

These will give you an idea of Sage's capabilities:
[http://www.sagenb.org/home/pub/354/](http://www.sagenb.org/home/pub/354/)
[http://www.sagenb.org/home/pub/566/](http://www.sagenb.org/home/pub/566/)

Note as I stated in my previous post I use Latex myself, but Sage is an interesting option that I'm considering to learn. If I want to embed some calculations to my documents I use Sweave [http://www.stat.uni-muenchen.de/~leisch/Sweave/](http://www.stat.uni-muenchen.de/~leisch/Sweave/)

I'm in teaching myself so I use it to write course material rather than handing in exercises, but I sure would be glad if the students handed in the reports written in something Latex based with decent graphics rather than MSword with excel graphs...

At least you can have a good laugh at your students for really putting tons of needless effort to generate their (ugly as heck) Figs., and their even more uglier Word doc. :D 

Give them a task involving matrix operations, or vector reshaping, and let them scratch their head in Excel. :p

---

### Post by ahmatti on 2009-07-20
> **XCan said:**
> At least you can have a good laugh at your students for really putting tons of needless effort to generate their (ugly as heck) Figs., and their even more uglier Word doc. :D 

Give them a task involving matrix operations, or vector reshaping, and let them scratch their head in Excel. :p

Sort of do get a laugh, but they are a pain in the *** to revise ;) And, yes in some of the classes it is forbidden to hand in exercises made with spreadsheet software. I do accept hand written stuff, but in some classes like simulation we only use Matlab.

---

