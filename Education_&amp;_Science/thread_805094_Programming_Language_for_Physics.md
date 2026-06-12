---
title: "Programming Language for Physics"
date: 2008-05-23
forum: Education &amp; Science
---

### Post by Berto88 on 2008-05-23
Hi, iv just finished my 2nd year in physics and over the summer wanted to try to learn a computer programming language for use with calculations etc. So far all i've used is basic java.

Has anyone got any suggestions on other languages that might be better?

---

### Post by tommers on 2008-05-23
Many computational physicists use C and C++.  I have also read that Fortran 95 has most of the same functionality as C++.

Depending on your programming experience, however, Python is probably the place to start... specifically visual python.  There are many good physics tutorials (using physics accessible to an an undergraduate major) that use visual python.  Just google visual python and physics, and you should find something good.

---

### Post by jpkotta on 2008-05-24
I recommend Octave/Matlab and Mathematica.  Unfortunately, Mathematica is commercial, but I like it better than Octave (or Matlab).

---

### Post by JudgeFudge on 2008-05-24
The only reason to switch to C or Fortran from Java for physics would be if your calculations are taking too long and you really want to improve the speed. With C++ (Fortran is actually faster than C++ for physics type work) you could see an improvement (like twice as fast) but only if you really know what you are doing with memory allocation and the like. Otherwise don't bother, Java is pretty fast for long iterative calculations and with the difficulty of debugging numerical errors avoiding the extra complexity of C/Fortran is beneficial.

On the other hand, if speed isn't a big issue, then Mathematica or Matlab (or there open source brethren Maxima, Octave, Scilab etc) or better than Java due to their native support for mathematical functions (and plotting - hugely  important). The difference between Matlab and Mathematica is that Mathematica allows a visually appealing symbolic contruction of equations and functions, whereas matlab is a bit faster. Also matlab's plotting is better.

Incidentally, matlab interfaces to fortran and C and mathematica to java - but both are pretty ugly. Scilab does a better job of talking to Fortran but is less solid.

---

### Post by tommers on 2008-05-24
The following resource letter appeared recently in the American Journal of physics... it seems pertinent to the discussion:

Resource Letter CP-2: Computational Physics
AJP -- April 2008 -- Volume 76, Issue 4, pp. 296-306

---

### Post by InfernalNeutrino on 2008-05-24
Hi,

I'm not sure what your future plans are, but I can at least offer my perspective as a grad student in nuclear physics (so depending on what field you want to go into, etc your mileage may vary). The most useful language for me has proven to be c++. Most of the simulation software I work with is written in it (geant4 and some home-grown software in particular), and it has proven useful in learning to use ROOT, a powerful analysis tool. Also, the data acquisition software I work with is primarily written in c++. Finally, after learning c++, I found learning fortran to be a rather simple affair, or at least learning as much of it as I need to handle the relatively few fortran programs I have to deal with. 

But I would also recommend learning a scripting language at some point. I've found Python to be extremely useful because I find it easy to write and easy to maintain. I use it for a variety of simple tasks, like parsing files or simple calculations. I don't really use mathematica or matlab much, and when I do it really is just for classes. To some extent though, this is just because I'm an experimentalist and only really care about doing detector simulations and analyzing data. Anyway, just my 2 cents

---

### Post by ssam on 2008-05-24
I am doing simulations for particle accelerator design. The main code i am using is written in FORTRAN, but I am using Python to generate input files, and analyse  output files.

python combined with numpy and matplotlib (available in the repos), gives you quite a handy language for doing numerical stuff. it lets you do all the things you can do in matlab (but without the (huge) cost).

---

### Post by Stochastics on 2008-05-24
Hi,

I'm a theoretical physics (quantum electrodynamics). One advice, if you have just two languages to learn, its C++ and Python. With these two, you can do a lot of things. Good luck ! and good work, because it's a great idea to learn a programming language early in your physics career.

Stochastics

---

### Post by lamborghiniwang on 2008-05-26
I am in the field of relativity and astrophysics, and I usually only use C/C++(with GSL, blitz++ and fftw libraries) if speed is the concern and use python for some quick/simple jobs. If you haven't, you may also want to learn one of the following: Mathematica, Maple or Matlab, which can be very useful while doing symbolic calculations and even some simply numerical works.

  btw, just my 2c, considering the current job market for physcists, I suggest you pay more attention to algorithm and C++, which will be useful in case you may have to look for jobs in other field (like financial engineering) in the future.

---

### Post by shiny2008 on 2008-05-27
Hi, 

I think, we can also use the C++ language for doing calculations. thank u

=============

detta

Looking to perform an intervention on a loved one who is abusing drugs or alcohol? This site can definitely help. 

[http://www.druginterventions.net]("http://www.druginterventions.net")

---

### Post by WaitingforGuiteau on 2008-05-27
I've hopped all over physics in my first two years in graduate school, and I can say that there are four languages that seem to be everywhere (five if you do high energy physics and use ROOT, or data analysis and use IDL, but I don't and I haven't):

(1) Mathematica/Maple: I know people that do relativistic hydrodynamic calculations for nuclei and they always start out with Mathematica. I personally don't like the syntax for more elaborate coding, I don't know why, it just doesn't stick very well. However, if you have to do some irritatingly elaborate integral, these two are a good start, and apparently they've got quite a bit of computational power as well.

(2) Python: This is my bread and butter language right now, because it's really fast to program something, the SciPy, NumPy and matplotlib libraries are incredibly useful, and, most importantly, if you have any programming experience at all you can pick up Python and do something productive with it over a weekend. My understanding, having never used Java, is that Python is what Java was supposed to be, but failed. It's faster, the libraries are useful (although sometimes the documentation is a bit lackluster), and it's free.

(3) C, C++, ForTran: For the heavier numerical stuff, which I will inevitably get into, everyone seems to use one of these three. They're fast, particularly ForTran which is designed just for scientists, but the programming can be a bit cumbersome. Honestly, most of the people I know don't go to these unless it's a last resort, because whatever you need to do you can probably get it coded and working in half the time with Python, unless you're trying to diagonalize million by million matrices or something else along those lines. One specific complaint I've heard about C is how it handles multi-dimensional arrays, which is to say poorly. Also, ForTran is falling out of favor because it's just very old.

(4) Octave/MatLab: Somewhere between Mathematica and Python are these guys. They don't do algebraic manipulation so well, but on the flip side they are optimized for numerical work. You don't get quite the flexibility and general ease of programming you'd get from Python, but personally I think they're faster on numerical work and the syntax is, at least to me, more intuitive than Mathematica.

The big thing to keep in mind is that physicists are open source nerds, so any format that is portable is going to be preferable. So categories 2 and 3, and to some extent 4, are going to be preferred because you can throw a .py file on a website, anyone can download and use it without having to pay a license, and everyone's happy.

---

### Post by nebu on 2008-05-28
if you want a low level language.... where u will have more control over the pc.... try c++

but if u want something fast.... and easy to type..... id say python..... it is also slightly easier to play around with large numbers in python than it is in c++

---

### Post by Frenske on 2008-06-06
Have a look around what other people in your area are using. Using the same language helps interaction and often scripts can exchanged.
As a geophysicist I was trained to use Fortran77 and till a year ago I used Fortran95 with Matlab to analyse the output files. I have changed jobs and use now C++ and Scilab for analyse.

---

### Post by lisati on 2008-06-06
I find it interesting to read that Fortran still rates a mention, a stripped down version of it was the first language I dabbled with thirty-something years ago. If memory serves correctly, it was originally designed for scientists & derives its name from "**FOR**mula **TRAN**slation"

Not being well versed in OOP programming, I'd probably lean towards C in preference to C++. Then again, depending on the kind of problem(s) you're working on some kind of OOP might have its advantages.....

Have a great day, everyone, and keep on smiling!

---

### Post by malvoria on 2011-08-24
Hi, I know that this topic is old, but maybe it will be of help to someone else...

I just coauthored a book on F# and game programming. The main subject of the book is the F# language and its various constructs, but every single chapter is centered around a physics simulation or game-related problem. Each one of the first 5 chapters describes a problem, shows and discusses its solution and then discusses in depth the F# constructs used. The book has a (relatively unique) "problem-solution" approach where everything is explained because of how well it works in solving the problem, and not just "because". The 5 problems we present are:
- a bouncing ball
- the Saturn V rocket
- an asteroid field
- a large asteroid field optimized with quad trees
- a police starship that must fight off a pirate ship attacking a cargo freighter
In the last two chapters we use XNA to build a 2D and 3D renderer for two of the samples we have seen. We show the basics of the SpriteBatch class, the Model class, input management and audio with this powerful framework. Basically, we cover the most important aspects of XNA in a simple and succint way. 

If you want to take a look at the samples, they can all be downloaded **freely** at: [http://fsharpgamedev.codeplex.com/](http://fsharpgamedev.codeplex.com/)
The great part of the code in the book has been developed and tested with Mono and MonoDevelop; chapter 6 should work with MonoXna (we have not tested it extensively). Only the last chapter is excluded.

The book is relatively short and cheap (166 pages and 7,49$) and can be found here [http://www.amazon.com/dp/B005HHYIWC](http://www.amazon.com/dp/B005HHYIWC) or here [http://www.smashwords.com/books/view/81765](http://www.smashwords.com/books/view/81765)

Thank you and I'm sorry if this message is not appropriate for this forum :oops: :oops:

Giulia

---

