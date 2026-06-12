---
title: "Command line software for basic statistics"
date: 2009-01-02
forum: Education &amp; Science
---

### Post by Jota37 on 2009-01-02
Hi,

Excuse me for a little bit of advertising for my little program, which I hope might be useful to someone else. If you get to use it, please let me know of any bugs you might find or possible improvements to suggest.

**The problem:**
I do work in bioinformatics/genomics and keep dealing with large tables of information (e.g. long tabular BLAST reports, which not uncommonly can have hundreds of thousands of rows). Sometimes, I'm interested in knowing some simple statistics about a certain column, say average, or the median, maximum and minimum values, etc. I do almost all my work on the command-line (many times on a remote computer), so I'd rather stay there. And anyway, firing up a spreadsheet program and opening a file just to do this takes quite some time -- and the spreadsheet program almost always has a low limit on the number of rows it can handle.

So, I thought, there should be a command-line program in *nix systems already written to do this, right? Use "cut -f" to get the column you want, then pipe the output to a program that will give you, say, the average or whatever. After a lot of "apropos" use, I concluded there was no such program already included. And web searching revealed nothing that simple, at least as far as I could find. Lots of libraries and complex, interactive software, but not what I was looking for. Well, at least I didn't find it (if you know of it, please let me know!).

**My solution:**

Scratching my own itch, I wrote a simple program for dealing with these problems. It's called "average" (I chose that very unimaginative name since there was nothing named like that in our GNU/Linux or other *nix computers here at the uni, so name conflict is less likely), and it is available [at Sourceforge]("http://sourceforge.net/projects/average/"), as usual.

**Quick description:**
Average is a simple and fast command-line Perl utility for calculating basic statistics on a list of numbers (one number per line of input, any non numerical data will be ignored), and it is licensed under the GPL v. 3. It works as a traditional Unix filter, and should work in any system where Perl is available. Average currently can: calculate the arithmetic mean; standard deviation; median; sum of all values; show the maximum and minimum values; and the total number of items (a.k.a "n"). The user can specify the number of decimal places to show in the results.

I hope anyone out there can find it useful. I use it all the time, and it saves me **a lot** of time. :-)

Thanks!

---

### Post by akniss on 2009-01-02
> **Jota37 said:**
> I do almost all my work on the command-line (many times on a remote computer), so I'd rather stay there. ... So, I thought, there should be a command-line program in *nix systems already written to do this, right? ... Well, at least I didn't find it (if you know of it, please let me know!).



Have you looked into R?
[http://www.r-project.org/](http://www.r-project.org/)

---

### Post by Jota37 on 2009-01-03
Hi, akniss

Thanks for the answer.

Yes, I know about R, we have used it for microarray analysis, for example (although I haven't learned the language). And it's exactly what I didn't want (complex, big, interactive -- or scriptable -- software) for such a simple task. What I wrote is something that can be used in a pipe, in a couple of seconds. R would probably be overkill (and it's not present in all systems here, for example, while Perl or a C compiler are), and more complex to use. Or so I think. Do you have a quick line to use R like this:

```
cut -f 1 table_file | average
```

That's what I do all the time, and before I was using a spreadsheet program, which was a drag.

---

### Post by akniss on 2009-01-03
> **Jota37 said:**
> Do you have a quick line to use R like this:
```
cut -f 1 table_file | average
```

```

mean(read.table('table_file')[,1])

```
I can see that your program is very efficient for the type of calculations you do.   However the nice thing about R is that it will do many simple tasks easily, in addition to doing very complex tasks.  The main difference is you typically need another terminal open that has R running, whereas you can just run yours from any terminal you happen to be in at the time.  For my workflow having R open is fine since I'm always using R for various tasks throughout the day.

---

### Post by UbuWu on 2009-01-03
> **akniss said:**
> The main difference is you typically need another terminal open that has R running, whereas you can just run yours from any terminal you happen to be in at the time.

Or you can use this:

r -e "mean(read.table('table_file')[,1])"

---

### Post by akniss on 2009-01-03
> **UbuWu said:**
> Or you can use this:

r -e "mean(read.table('table_file')[,1])"

Thanks for the suggestion... I wasn't aware of the littler package prior to reading your post.  It will likely be quite helpful to me, even if not for the OP.  However, on my system I must actually call the print() command to get any output from the littler package:

```
r -e 'print(mean(read.table("table_file")[,1]))'

```

---

### Post by raja on 2009-01-03
Kudos to the author for the effort! However, I am adding another vote in favor of R. If you are an emacs user, then you have an emacs running all the time and all you need to do is start ESS in a buffer. 
After having tried out JGR and Rcmdr and then settling down to running R from the terminal, I finally found ESS on Emacs and it is simply fantastic. Sorry if I veered off topic.

---

### Post by euler_fan on 2009-01-03
There is [a major bioinformatics project]("http://www.bioconductor.org/overview") which uses R as a springboard . . . and if you're particularly into that field there may be a case to get R and the required packages for your work installed on you machine (but it doesn't sound like you have one) or all of them in a given department-owned computer lab to which you have access. It helps that all of this is free software :)

If on the other hand you're stuck working at arbitrary machines around and about then your answer is probably optimal, sadly, even if it requires reinventing the wheel.

---

