---
title: "What programming features do scientists need?"
date: 2011-03-18
forum: Education &amp; Science
---

### Post by chapter34 on 2011-03-18
Calling all scientists for a brain dump -- if you had the chance to shape the development of a new programming language, what would you do differently? I'm after everyone's ideas please, no matter how wild or apparently infeasible.
 
Features, syntax, mode of operation, etc. I already have well formed opinions of many of the mainstream programming languages, and none of them get everything quite right. And that bothers me. Because it is possible to get the right mix. But I'm also after wilder non-conventional ideas that no programming language has ever done. If there are any.
 
So, please use this thread to discuss your programming dreams. You never know, some of those might then become a reality ...
 
Not wanting to sway any of your ideas, but I've started right at the bottom and developed a bytecode, interpreter for said bytecode, and associated assembly language. I'll stay at that level for a good time to come, until it provides all the basics I need to implement all of your best ideas:
 
[http://prose.sourceforge.net](http://prose.sourceforge.net)
 
Best regards,
Mark Bannister.

---

### Post by Lateralis on 2011-03-18
Hi Mark.  Interesting project idea that.  At the moment I only ever need to code in Perl which I find amazingly useful and powerful.  

Most of the code I don't write myself is usually written in Fortran or C, but in those instances I just compile the code.  

From a personal point of view the only problem I have with Perl is it isn't so easy to make graphs from.  I use Perl mostly for data handling, extraction, transformation and the like and I've often wanted to make popup and interactive graphs from these data, just so that I can "eyeball it" - check to see if its garbage or not.  So far I've not had the time to investigate graphing using Perl modules but from what I can tell it isn't so easy.  

So, from my point of view, a programming language that has all of the (modular) functionality of Perl coupled with a nice plotting functions that are simple and easy to use would be rather nice!  But aside from that, I'm more than happy with Perl.

---

### Post by chapter34 on 2011-03-25
Do you find the Perl syntax helpful, or is it a hindrance?  Out of interest, how complicated are the Perl scripts you write?  Would you say they're generally not modular and less than 1,000 lines long each?  What programming language would you choose if you wanted to write an application that involved a team of 10 programmers and over 100,000 lines of code split across 50+ modules?  Would you still choose Perl for a job like that?
 
If someone else had to pick up your Perl scripts in the future, understand them and modify them, would you think they'd be able to understand your scripts very quickly, or are you using syntax that obfuscate the code's purpose?

---

### Post by Lateralis on 2011-03-25
I personally find the Perl syntax a great help.  It is very clear and straightforward.  The one part that caught me a little off-guard to begin with was printing 2D arrays, but that was just a momentary stumbling block in my learning experience. 

As for my scripts, no, they're generally not that complicated and generally not that long.  I don't suppose I'm really the target audience you had in mind (but I tried to say that in my previous post).  I think all of my scripts are less than 1000 lines long and do not use modules I have written.  I do make use of other people's modules though (and therein lies one of the key strengths of Perl...).  The scripts that I write are mainly for data handling and manipulation: extraction of specific data from simulated data outputs, generation of input files for simulation codes, generation of files for crystal structure visualisation from simulation input files, theoretical x-ray diffraction peak positions and a bunch of CGI scripts for an interactive website for colleagues and collaborators.  

All of my codes are well commented for future users.  I don't distribute most of my codes as they are mainly to help me, but of the scripts I have given to collaborators and my supervisor they are all commented and clearly laid out.  Some "difficult" bits of some codes have links or references to online documentation for further reading.  So I would say in general the codes I have given out are easy to follow.  

As for which programming I would use for a major project, I'm unsure.  For major projects C and Fortran seem to be the two languages used most often in the simulation software packages I use, i.e DFT codes like SPRKKR, CASTEP, Exciting and other programmes like Fdnmes.  Would I choose to do a project in Perl?  Probably yes but it would depend on the project and what the absolute time cost is of running the code in Perl relative to another language like Fortran or C.  Would I ever work as part of a project team: probably not!

---

### Post by cheetaux on 2011-03-25
I'm an engineer who has programmed in Fortran, C, C++, Ada, Pascal, Java, Ada, Perl, and most recently Python (and probably a few others).  I find that Python with the NumPy and SciPy extension is extremely powerful and user friendly.  NumPy and SciPy provide just about everything you would need (matrix math, FFT, special functions, etc.)  Give Python a try!

---

### Post by cheetaux on 2011-03-25
After re-reading the original post, I see that the question is what features do scientists need, not what programming language.

Well, I think Python has most of the features needed.  One recommendation though: start array indices at one (like Fortran), not at zero as C/C++ and Python do.

---

### Post by Claus7 on 2011-03-25
Hello,

> **chapter34 said:**
> 
So, please use this thread to discuss your programming dreams. You never know, some of those might then become a reality ...
 
Best regards,
Mark Bannister.

I would not like to ruin your thread, yet I got a glimpse of the sentence above, and if we take into account science fiction as well (anyone remembers star trek?), what I would like to see would be a ...hmmm how I can describe it? An image processing unit, which will transform 3D objects drawn to a computer to real life materials. That way they might be more easier to analyse or helping to get a real picture about what is being processed on a computer screen.

With all due respect to all the people who wrote, write and will write on this thread.

Regards!

---

### Post by Lateralis on 2011-03-26
Perl also starts matrices from zero.  To be honest, I like that.  I've got used to it!  Also, Perl has a number of modules that can perform anything you like, including FFT etc.  The power of CPAN!

---

### Post by cwarner7_11 on 2011-04-23
A traditional problem I have faced, and for which I have never found a really adequate solution, involves data acquisition- especially, getting down into the real capabilities of the machine to grab data from external devices- like trying to use the internal clock to time the acquisition.  Most languages have some reasonable data acquisition functions (c, Fortran, even Basic), they generally are cluttered with structured read/write formatting that can really slow things down.  Other than pure assembler, about the closest I have found to a language that really unlocks the full capabilities of the hardware would be Forth.

---

### Post by Lateralis on 2011-04-24
From what kind of hardware are you trying to acquire data?  This maybe nowhere near what you want, but [*spec*]("http://www.certif.com/spec.html") may do what you want.  It is a UNIX-developed software package which is used [extensively at synchrotrons and elsewhere]("http://www.certif.com/places.html") to automate motor movements and acquire experimental data.  I've used the software at X13A and X22C at the NSLS and it works well.

---

### Post by cwarner7_11 on 2011-04-24
> **Claus7 said:**
> Hello,



"An image processing unit, which will transform 3D objects drawn to a computer to real life materials..."

Already exists- I have been using such technology since the late 1980's.  It is called "3D Printing" or "Rapid Prototyping", and you can build your own from kits or from scratch for something like $2000 (limited materials options, usually), or you can spend several hundred thousand dollars to buy a more sophisticated machine that is capable of producing articles from 3D CAD designs in a surprizing variety of materials...

---

### Post by Claus7 on 2011-04-24
Hello!

> **cwarner7_11 said:**
> Already exists- I have been using such technology since the late 1980's.  It is called "3D Printing" or "Rapid Prototyping", and you can build your own from kits or from scratch for something like $2000 (limited materials options, usually), or you can spend several hundred thousand dollars to buy a more sophisticated machine that is capable of producing articles from 3D CAD designs in a surprizing variety of materials...

the next time I'll ask from ubuntu forums, how is it possible to win the first year's lottery! Who knows? I might win!

Thanks a lot! It did never crossed my mind that something like that existed.

Kind regards!

---

### Post by rich-york on 2011-04-25
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=Lucida Grande]Very interesting, thank you for sharing!

Richard
[/FONT][/COLOR][/FONT][/COLOR]

---

