---
title: "C programming class"
date: 2010-08-24
forum: Education &amp; Science
---

### Post by fkachinski on 2010-08-24
I'm taking an intro to C class. I have software to write and compile on vista, but I'd like to use my laptop with ubuntu to write and run the programs. How can I do that? I'm looking for a very simple and complete step by step. I don't have a lot of experience with the inter workings of ubuntu yet. 
Thanks guys

---

### Post by lordhaworth on 2010-08-25
Hi,

There will be many ways of doing this and it depends on what you want...

One way involves using a text editor and compiling/running etc in terminal:

You can write your C programs in a text editor - I would recommend "Emacs":

[http://riddell.us/EmacsOnUbuntu.html](http://riddell.us/EmacsOnUbuntu.html)
[http://www.gnu.org/software/emacs/](http://www.gnu.org/software/emacs/)

There is a good tutorial which will help you get used to using it built in.  

To compile/run your code - see this thread:
[http://ubuntuforums.org/showthread.php?t=29698](http://ubuntuforums.org/showthread.php?t=29698)


Another way involves getting some "integrated development environment" IDE (whcih is likely what you had in vista) in which you do all of your coding/compiling/editing. See e.g. "Eclipse".

[http://www.eclipse.org/downloads/?osType=linux](http://www.eclipse.org/downloads/?osType=linux)

Using the above link choose the "Eclipse IDE for C/C++ Developers"


Any further questions let us know - It might also be worth posting in "Programming Talk" (Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Development & Programming > Programming Talk)

---

### Post by Silentvoice on 2010-08-25
Emacs isn't something I would recommend to a beginner. That's something you decide to start using once you've programmed for a while, and you have gains to be had by using a powerful text editor. 

I would recommend Geany. Simple windows-like interface, and it has all the basic features that Visual Studio has that beginners to C are likely to take advantage of.

---

### Post by matthew.ball on 2010-08-25
I don't understand this mantra which is attached to GNU Emacs.

Trust me, if I can learn to use it, anyone can. It'd be especially useful to a beginner.

The exact argument you give for using Geany applies equally well to using GNU Emacs. Have you actually used it yourself, or are you just sprouting stuff that you've read posted?

This is not to say that one should go out and learn all there is to know about GNU Emacs - something I don't think is possible even for veterans - it's exactly the same as any other application, just learn what you find comfortable and that's enough. You will pickup new knowledge as you go along. This is natural.

---

### Post by GregBrannon on 2010-08-25
Mantra?  Do you mean stigma?

---

### Post by matthew.ball on 2010-08-25
> **GregBrannon said:**
> Mantra?  Do you mean stigma?
Either works, but I did mean it in the sense that it's like a sacred belief that only Unix elites should be using GNU Emacs because it's "apparently" so difficult.

In that context, I think it's closer to the definition of mantra than stigma. I could be wrong though.

---

### Post by Silentvoice on 2010-08-25
> **matthew.ball said:**
> I don't understand this mantra which is attached to GNU Emacs.

Trust me, if I can learn to use it, anyone can. It'd be especially useful to a beginner.

The exact argument you give for using Geany applies equally well to using GNU Emacs. Have you actually used it yourself, or are you just sprouting stuff that you've read posted?

This is not to say that one should go out and learn all there is to know about GNU Emacs - something I don't think is possible even for veterans - it's exactly the same as any other application, just learn what you find comfortable and that's enough. You will pickup new knowledge as you go along. This is natural.


I've used emacs, I have to on many machines at my school. I'm not saying it's a bad text editor, but I don't recommend it to just anyone. In this case it sounds like the fellow interested is familiar with windows, and so I just think it's more appropriate to recommend something that he'll be familiar with right off the bat, and let him make the decision to move into unfamiliar ground should it become important.

Were the post different I probably would have said vi or emacs, but in this case I think a more windows-user friendly environment would be more appropriate.

---

### Post by lordhaworth on 2010-08-26
I like emacs but have to agree it is difficult at first IMO. 

Someone moving from windows will likely wind up shouting at their computer when they find that they are failing to do something apparently simple like copy (Ctrl+c) and paste (Ctrl+v).


Thats why you do the tutorial first. It is also why I suggested an IDE such as Eclipse to someone who is used to working in windows

---

### Post by matthew.ball on 2010-08-26
> **lordhaworth said:**
> Thats why you do the tutorial first.
No, this is it exactly. If they're coming from Windows, chances are they don't have the foggiest idea how a console-based text editor would work - so to come in with such assumptions is entirely unfounded.

Have a go at the tutorial, and exactly as it says it is an *interactive* tutorial, you don't just read through it and commit the key combinations to memory. You need to get a feel for the controls.

It's certainly not difficult. I can say, with a great deal of certainty, that a very high percentage of the people on this forum are far more intelligent than I am, and like I said in the earlier post, if I can learn to use something, literally anyone can.

---

### Post by lordhaworth on 2010-08-26
> 
No, this is it exactly. If they're coming from Windows, chances are they don't have the foggiest idea how a console-based text editor would work - so to come in with such assumptions is entirely unfounded.

Have a go at the tutorial, and exactly as it says it is an interactive tutorial, you don't just read through it and commit the key combinations to memory. You need to get a feel for the controls.

It's certainly not difficult. I can say, with a great deal of certainty, that a very high percentage of the people on this forum are far more intelligent than I am, and like I said in the earlier post, if I can learn to use something, literally anyone can. 


Oh yes, I do agree - you can definitely dive into it without difficulty. I have been using it for a couple of years and only recently used the tutorial (but I found it helpful).

---

### Post by lordhaworth on 2010-08-26
I should also note that I never use an IDE - I am just presenting options

---

### Post by Lars Noodén on 2010-08-29
> **lordhaworth said:**
> I like emacs but have to agree it is difficult at first IMO. 

Someone moving from windows will likely wind up shouting at their computer when they find that they are failing to do something apparently simple like copy (Ctrl+c) and paste (Ctrl+v).


Thats why you do the tutorial first. It is also why I suggested an IDE such as Eclipse to someone who is used to working in windows

Eclipse and Emacs are great.

However, I would second the recommendation for Geany and also mention Kate.  At the basic level of teaching, the students are not going to need to be working with the full capabilities of an IDE.  It is enough to write a simple program or two, compile, debug, and run.

---

### Post by Zirts on 2010-08-29
Whats wrong with GCC?

---

### Post by lordhaworth on 2010-08-29
> Whats wrong with GCC? 

I may be horrendously mistaken, but isn't that just a compiler?

e.g. write in emacs compile with 

```

gcc code.c -o codeExec

```

---

### Post by Lars Noodén on 2010-08-30
> **Zirts said:**
> Whats wrong with GCC?

Not much.  It's been the best compiler on the market for many years and still is.  

geany and kate are not compilers.  They are simple editors with a bit of syntax highlighting and other small tricks that help programming.  You can even open a teeny-tiny console underneath your editing and see the output from your program.  

Kate has a lot of plugins and extensions for special tasks, I'm much less familiar with Geany, but expect that it is similarly flexible.

---

### Post by lisati on 2010-08-30
<nostalgic aside>
We can be thankful for having a choice of IDEs. When I started programming, the only option available for many students was punched cards or "card images" stored on disk. These were submitted to a computer somewhere that the first-year students usually didn't have direct access to, and you had to wait for what seemed like an eternity for your programming masterpiece to be processed, and then the output (often printed) was returned to you. No interacting with the compile-and-run process - if there was a problem, you had to punch up replacement cards and resubmit the whole lot. If you were lucky, you could look through a window into the computer room.
</nostalgic aside>

---

### Post by addy digit on 2010-10-06
I don't know if anyone else has said this but I guess I will. College courses are meant to show you the way for when you get into the professional world. Many companies today train their employees in the technologies they use. College courses are mean to give you some knowledge of it and the company will give you the rest.

---

