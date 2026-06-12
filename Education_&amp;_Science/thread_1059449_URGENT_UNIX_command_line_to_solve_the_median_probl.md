---
title: "URGENT: UNIX command line to solve the median problem."
date: 2009-02-03
forum: Education &amp; Science
---

### Post by patrick chia on 2009-02-03
My input:
10
15
20

My desired output:
Median = 15


**From the three figures in above, I know that 15 is the median. How can I use the UNIX command line to find it out automatically? My senior is advised me can use the 'awk' command line and the 'if' 'else' condition at the same time. Hope any UNIX expert can help me solve this problem and give me correct command line that I should used. Really thanks a lot for your help.

---

### Post by sisco311 on 2009-02-03
[thread=717011]Homework?[/thread]

Yes, you can solve it with awk. You don't need if/else statements.

[http://www.gnu.org/software/gawk/manual/gawk.html]("http://www.gnu.org/software/gawk/manual/gawk.html")

The arithmetic mean of a list of numbers is the sum of all of the list divided by the number of items in the list. ;)

---

### Post by gunksta on 2009-02-03
> **sisco311 said:**
> [thread=717011]Homework?[/thread]
The arithmetic mean of a list of numbers is the sum of all of the list divided by the number of items in the list. ;)


Although your math is perfect, the OP is looking for the median, not the mean. :D

I don't use awk unless I absolutely have to. There are a zillion ways to force a computer to find the median. OpenOffice.org Calc can certainly do this, although it's hardly a unix command line application. It's not overly difficult to write a simple script in python to find the median value, but you do have to be careful. Being lazy, I would not bother writing a script to calculate the median value of a list. Instead, I would use a program like R to calculate the median. Another option is PSPP. Since you specifically asked for "command-line", I'll show you how to do this in R. First, we will need to install it. 
```
sudo apt-get install r-recommended
```
You can start R with the command . . . . . "R" at the command prompt. The following syntax will return the median value in a list.
[INDENT]> options(STERM='iESS', editor='emacsclient')
> example <- c(10, 15, 25)
> median(example)
[1] 15
[/INDENT]Let's break this down. The first line isn't necessary. It just tells you that I use Emacs to interact with R. Lines 2, 3 are actual R syntax. Row 4 is R telling me that 15 is the median.

Of course, your example is the easiest possible case, because it has an odd number of elements. Here's another example.
[INDENT]> example <- c(10, 15, 25, 17)
> median(example)
[1] 16
[/INDENT]Median is a funny thing. Used correctly it _can_ be a useful measure of central tendency. But, it can also be kinda funny and mis-leading. As a policy analyst, I often use it to compare things like income, because it is not affected dramatically by outliers in the same way the mean is.

If this is for a school assignment, I would be curious to learn where / what class. I do enjoy it when professors ask their students to use command-line tools. For extra credit you can sit down tomorrow and show me how to calculate the median in PostgreSQL or MySQL.

---

### Post by xadder on 2009-02-04
... and I have saved many weeks (months) of work over my life by using the command line extensively. Who wants to open OOcalc or R every time a small job is needed? And especially if one has 100s of files to process, which I often do.

I must admit didn't spot an elegant solution yet to this problem with awk though, but as usual one can adopt the unix way and string together small commands. I use csh, and the following works for a data-file with an odd number of lines:

set n=`wc input_file` && sort -n input_file | awk '{if(NR==(N+1)/2) print  }' N=$n[1]

First $n is set to the number of lines in the file. Actually to "3 input_file", so we need $n[1] to extract the number 3. (I don't know bash well enough to get that, but I presume this is trivial).

I added sort -n in case the data are not in numerical order. If you have to cope with both odd and even number of lines, you will need an if, else construction in awk. Then it starts getting messier, and I would have written a perl/python script for that.

If you know you have 3 lines, then it is trivial:

awk '{if(NR=2) print }' input_file

(Beat that for speed, R, OOcalc!)

The above example is slightly messy I admit, but awk is often great for small jobs, e.g. to find the sum of the numbers in 3rd column of a file:

awk '{ tot += $3 }END{ print tot }' input_file

To find the max:

awk 'BEGIN{max=-999e19} {if($3>max) max=$3}END{print max}' input_file

etc.

---

### Post by ahmatti on 2009-02-04
Great examples xadder! I agtee with you that command line saves you a lot of time for small jobs like this, eventhough I do use R for bigger problems.

Patrick, this thread has exactly what you need, its a command line software written in Perl just for your purpose (the name of the tool is average, but it can also calculate the median):
[http://ubuntuforums.org/showthread.php?t=1028667](http://ubuntuforums.org/showthread.php?t=1028667)

---

### Post by gunksta on 2009-02-04
R is easy to script and I often use it for small jobs simply because it's easy to use. I prefer to re-use tested code rather than over-think easy problems.   I prefer:

```
median(k)
```over
```
set n=`wc input_file` && sort -n input_file | awk '{if(NR==(N+1)/2) print  }' N=$n[1]
```There is also the added advantage that I know R correctly handles lists with an even number of elements. With ad-hoc solutions (solutions not included in a distributed program or library) I would first have to read / understand the code to be sure that it operated correctly. 

If R is simply too much effort, I would also recommend googling for numpy, which can also calculate the median. I didn't think of it last night when I wrote my original reply. Since it is a python library, it might appeal more to people who believe R is too difficult to script (although I don't understand this at all). There is probably something similar for perl but I don't know perl very well.

EDIT: Regarding the thread referred to by ahmatti, I find it interesting that most of the responses are examples of how to use R to do the same thing. :-)  But, I want to thank ahmatti for posting this thread here, because I have now learned about the "little r" program, which is designed to help you use R in a bash script. The number of uses to this little trick are incredible.

---

### Post by patrick chia on 2009-02-04
> **xadder said:**
> ... and I have saved many weeks (months) of work over my life by using the command line extensively. Who wants to open OOcalc or R every time a small job is needed? And especially if one has 100s of files to process, which I often do.

I must admit didn't spot an elegant solution yet to this problem with awk though, but as usual one can adopt the unix way and string together small commands. I use csh, and the following works for a data-file with an odd number of lines:

set n=`wc input_file` && sort -n input_file | awk '{if(NR==(N+1)/2) print  }' N=$n[1]

First $n is set to the number of lines in the file. Actually to "3 input_file", so we need $n[1] to extract the number 3. (I don't know bash well enough to get that, but I presume this is trivial).

I added sort -n in case the data are not in numerical order. If you have to cope with both odd and even number of lines, you will need an if, else construction in awk. Then it starts getting messier, and I would have written a perl/python script for that.

If you know you have 3 lines, then it is trivial:

awk '{if(NR=2) print }' input_file

(Beat that for speed, R, OOcalc!)

The above example is slightly messy I admit, but awk is often great for small jobs, e.g. to find the sum of the numbers in 3rd column of a file:

awk '{ tot += $3 }END{ print tot }' input_file

To find the max:

awk 'BEGIN{max=-999e19} {if($3>max) max=$3}END{print max}' input_file

etc.
The command line you given can't find the median, max and total sum. You got any other better suggestion? Anywhere thanks for your advise. Have a nice day.

---

### Post by patrick chia on 2009-02-04
> **sisco311 said:**
> [thread=717011]Homework?[/thread]

Yes, you can solve it with awk. You don't need if/else statements.

[http://www.gnu.org/software/gawk/manual/gawk.html]("http://www.gnu.org/software/gawk/manual/gawk.html")

The arithmetic mean of a list of numbers is the sum of all of the list divided by the number of items in the list. ;)

You got any other better way to find out the median? Thanks for your advice. Hope can receive your reply soon.

---

### Post by patrick chia on 2009-02-04
> **gunksta said:**
> Although your math is perfect, the OP is looking for the median, not the mean. :D

I don't use awk unless I absolutely have to. There are a zillion ways to force a computer to find the median. OpenOffice.org Calc can certainly do this, although it's hardly a unix command line application. It's not overly difficult to write a simple script in python to find the median value, but you do have to be careful. Being lazy, I would not bother writing a script to calculate the median value of a list. Instead, I would use a program like R to calculate the median. Another option is PSPP. Since you specifically asked for "command-line", I'll show you how to do this in R. First, we will need to install it. 
```
sudo apt-get install r-recommended
```
You can start R with the command . . . . . "R" at the command prompt. The following syntax will return the median value in a list.
[INDENT]> options(STERM='iESS', editor='emacsclient')
> example <- c(10, 15, 25)
> median(example)
[1] 15
[/INDENT]Let's break this down. The first line isn't necessary. It just tells you that I use Emacs to interact with R. Lines 2, 3 are actual R syntax. Row 4 is R telling me that 15 is the median.

Of course, your example is the easiest possible case, because it has an odd number of elements. Here's another example.
[INDENT]> example <- c(10, 15, 25, 17)
> median(example)
[1] 16
[/INDENT]Median is a funny thing. Used correctly it _can_ be a useful measure of central tendency. But, it can also be kinda funny and mis-leading. As a policy analyst, I often use it to compare things like income, because it is not affected dramatically by outliers in the same way the mean is.

If this is for a school assignment, I would be curious to learn where / what class. I do enjoy it when professors ask their students to use command-line tools. For extra credit you can sit down tomorrow and show me how to calculate the median in PostgreSQL or MySQL.
gunksta,
Do you have any better easier way to find out the median? My teacher only allow us to use the command line or type the program in script to find out the median. I will appreciate for your advice.

---

### Post by patrick chia on 2009-02-04
> **ahmatti said:**
> Great examples xadder! I agtee with you that command line saves you a lot of time for small jobs like this, eventhough I do use R for bigger problems.

Patrick, this thread has exactly what you need, its a command line software written in Perl just for your purpose (the name of the tool is average, but it can also calculate the median):
[http://ubuntuforums.org/showthread.php?t=1028667](http://ubuntuforums.org/showthread.php?t=1028667)
Ahmatti,
You can type out the perl that you mention? Sorry I just start to learn the UNIX. Still very fresh for this operating system. That's why feel very stress when given this homework by my lecturer. Hope you can give me a better suggestion. Thanks a lot.

---

### Post by patrick chia on 2009-02-04
> **gunksta said:**
> R is easy to script and I often use it for small jobs simply because it's easy to use. I prefer to re-use tested code rather than over-think easy problems.   I prefer:

```
median(k)
```over
```
set n=`wc input_file` && sort -n input_file | awk '{if(NR==(N+1)/2) print  }' N=$n[1]
```There is also the added advantage that I know R correctly handles lists with an even number of elements. With ad-hoc solutions (solutions not included in a distributed program or library) I would first have to read / understand the code to be sure that it operated correctly. 

If R is simply too much effort, I would also recommend googling for numpy, which can also calculate the median. I didn't think of it last night when I wrote my original reply. Since it is a python library, it might appeal more to people who believe R is too difficult to script (although I don't understand this at all). There is probably something similar for perl but I don't know perl very well.

EDIT: Regarding the thread referred to by ahmatti, I find it interesting that most of the responses are examples of how to use R to do the same thing. :-)  But, I want to thank ahmatti for posting this thread here, because I have now learned about the "little r" program, which is designed to help you use R in a bash script. The number of uses to this little trick are incredible.

gunksta,
You know what is R program? Actually this is my first time listen about it. Hope you can provide me some source or tutorial to further understand about it. Thanks a lot for your help.

---

### Post by gunksta on 2009-02-04
R is a terrific tool for data analysis. R has a couple of options for scripting. The littler option mentioned previously is harder to use, because you have to install additional stuff into the system. I would probably not recommend this for right now. Instead, I would look at Rscript. To learn more enter:

```
man Rscript
```

after you have installed R. The man page is useful. If you have already started R, then you can use:

```
?Rscript
```

Your other is to write an executable script that can use R, in the same way a python script uses python. In the first line of your script you will need something that looks like:

```
#! /usr/bin/Rscript
args <- commandArgs(TRUE)

blah blah blah blah blah

#q(status=<exit status code>)
```

If you want you learn R, I would recommend two resources. First, _the_ PDF on R is:
[http://cran.r-project.org/doc/manuals/R-intro.pdf](http://cran.r-project.org/doc/manuals/R-intro.pdf)

Secondly, there is the site [Quick-R]("http://www.statmethods.net/input/variablelables.html"). This second resource is especially useful to anyone with a background in SPSS / PSPP.

Since this _is_ a homework assignment, I don't want to give the whole shebang away, and I have technically told you how to write 90% of the script already. I'll let you read R-intro. It's boring but informative. The stuff in the very back discusses scripting R from the command line.

If you have any specific questions, feel free to post them, but do be aware that the Ubuntu Forums do have a policy against answering homework questions directly/completely.

---

### Post by ahmatti on 2009-02-05
Patrick,
Follow this link: [http://sourceforge.net/projects/average/](http://sourceforge.net/projects/average/) (its from the thread I pointed). 

Gunksta,
I don't think R is too difficult to script and I use it daily, but for some problems command line tools are a lot faster to use. Especially if I just want to find simple things from large data files I don't always want to wait for R to start and read in the whole 200 Mb file just to find the average etc..

---

### Post by xadder on 2009-02-05
Patrick Chia,

What do you mean, the command line stuff I suggested can't find the median, max or sum? It does on my computer so I guess it will on yours. As I said, the complex line was in csh, not bash, and tat was just used to get the number of lines into the variable $n. (Maybe you have to type "csh" first).

The simple awk lines (for sum or max) will work in any shell.

---

