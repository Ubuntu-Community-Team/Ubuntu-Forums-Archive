---
title: "GUI or CLI for R"
date: 2007-08-12
forum: Education &amp; Science
---

### Post by euler_fan on 2007-08-12
I see threads getting posted or posted to pretty regularly about some update to a gui for R.

So, I thought I would ask a question of the R users out there:

Gui or no gui? Why?

I'll start:

1) I actually like the command line in interactive mode.
2) Batch execution of scripts rocks--and makes it really easy to replicate work at a later date.
3) I am always writing some custom stuff and would end up needing to run it all from the command line anyway.

---

### Post by edoviak on 2007-08-13
I agree with all of your reasons for writing scripts/using the command line. 

"Scriptless" packages like SPSS and EViews drive me crazy because it's difficult to keep track of your manipulations to the dataset when you don't write a script. And I'm no fan of Stata. I hate having to copy and paste line after line into the prompt when I'm just trying to test out a few lines. (Note: I've only used the MS Windows version of Stata. Is the GNU/Linux version any different?).

That having been said, I prefer to use a GUI (specifically RKWard) because it has the best of both worlds. RKWard's dialog boxes help me use the parts of R that I don't know very well (like plotting). I also like the way RKWard is organized. It keeps all of your variables neatly on the side and you can use tabs to pull up/drop down the console, help menus, command log, etc.

Of course, RKWard also allows you to run a script as batch, run parts of a script (to test them out) and type directly into a command line.

Who knows? Maybe one day I'll finally sit down to learn Emacs and my opinion will change. Until then, I'm also curious to know what others think.

- Eric

---

### Post by mali2297 on 2007-08-13
I use the CLI, mostly from habit. Since I'm comfortable with it, I haven't bothered to investigate the possible GUI alternatives. 

I know, it's not much for a reason.

---

### Post by euler_fan on 2007-08-13
I usually use Cream which has a nice syntax highlighting scheme and then source my scripts into R.

Between the debug flags, traceback, and a few other little tricks (like having it print "Line X Executing Now" pretty regularly testing stuff out and debugging has gotten much faster and easier.

One of these days I may get around to finally figuring out Emacs/ESS . . .

---

### Post by earlycj5 on 2007-08-13
> **edoviak said:**
> I agree with all of your reasons for writing scripts/using the command line. 

"Scriptless" packages like SPSS and EViews drive me crazy because it's difficult to keep track of your manipulations to the dataset when you don't write a script. And I'm no fan of Stata. I hate having to copy and paste line after line into the prompt when I'm just trying to test out a few lines. (Note: I've only used the MS Windows version of Stata. Is the GNU/Linux version any different?).

That having been said, I prefer to use a GUI (specifically RKWard) because it has the best of both worlds. RKWard's dialog boxes help me use the parts of R that I don't know very well (like plotting). I also like the way RKWard is organized. It keeps all of your variables neatly on the side and you can use tabs to pull up/drop down the console, help menus, command log, etc.

Of course, RKWard also allows you to run a script as batch, run parts of a script (to test them out) and type directly into a command line.

Who knows? Maybe one day I'll finally sit down to learn Emacs and my opinion will change. Until then, I'm also curious to know what others think.

- Eric

I have to agree with Eric.

RKWard is nice, I have several tabs open at once, different script files, help files, etc.

I don't think I've ever used the menu-driven functions, I just use it to write scripts.

Just easier for me to organize my thoughts and what I'm doing by using it with the way I work.

The "Export to HTML" feature was invaluable to me for syntax highlighting scripts when we started writing our web modules that teach how to use R and concepts in plant pathology epidemiology.  Definitely cleaned up the code and made it much easier to read on the web site.

---

### Post by euler_fan on 2007-08-13
I might have to take another look at RKWard then . . . 

It sounds like it has similarities to Emacs/ESS without getting all of Emacs' quirks.

---

### Post by akniss on 2007-08-13
I guess I have no problem with GUIs for statistical packages, as long as there is still access to the underlying language. In this respect, I think rkward is on the right track... making simple analyses and data manipulations accessible through the GUI, but allowing more complex customizations available through direct access to the R language.  Any stats package that REQUIRES point and click is worthless for anything but the most basic needs in my opinion, but one that ALLOWS point and click to go along with a powerful underlying programming interface will have a fit in many statisticians tool boxes.

---

### Post by edoviak on 2007-08-14
> **euler_fan said:**
> I might have to take another look at RKWard then . . . 

Thinking back on all the help you gave me to install the latest version of RKWard ...**[COLOR="Red"] I hope you enjoy it![/COLOR]** :)

One work of caution however: I had some difficulties installing RKWard 0.4.7a on Kubuntu Feisty. [**[COLOR="Navy"]Here's a link to the post.[/COLOR]**]("http://ubuntuforums.org/showthread.php?p=2938747#post2938747") That was my first attempt at compiling an application from source and, in retrospect, I wonder if I would have had more success had I used **# apt-get build-dep rkward** 

More recently however, I installed Kubuntu Feisty on my wife's computer and then immediately compiled RKWard 0.4.7a from source (i.e. before applying any updates to Kubuntu). The compilation went flawlessly.

Hope it goes well for you! Enjoy!
- Eric

---

### Post by earlycj5 on 2007-08-14
> **akniss said:**
> I guess I have no problem with GUIs for statistical packages, as long as there is still access to the underlying language. In this respect, I think rkward is on the right track... making simple analyses and data manipulations accessible through the GUI, but allowing more complex customizations available through direct access to the R language.  Any stats package that REQUIRES point and click is worthless for anything but the most basic needs in my opinion, but one that ALLOWS point and click to go along with a powerful underlying programming interface will have a fit in many statisticians tool boxes.

I agree wholeheartedly.  That's why I like RKWard.  Sure it's a "GUI" but it doesn't hide R from me at all.

Just makes it easier for me to edit and run script files more efficiently.

---

### Post by meatpan on 2007-08-15
I've always used the command line for R.  I try to keep the R scripts simple and with as little data munging as possible, so a better gui wouldn't help me much.  

Running R via batch scripts  would be much easier if the program could take and parse arbitrary variables from the command line.   Right now I kluge this behavior by setting and getting env variables.

---

### Post by euler_fan on 2007-08-15
> **meatpan said:**
> I've always used the command line for R.  I try to keep the R scripts simple and with as little data munging as possible, so a better gui wouldn't help me much.  

Running R via batch scripts  would be much easier if the program could take and parse arbitrary variables from the command line.   Right now I kluge this behavior by setting and getting env variables.

Is there a way to do this with Perl or Bash scripts? Have the script start R regularly, source in the appropriate script, and feed it the right values? If so it would automate any number of things.

---

### Post by meatpan on 2007-08-15
That is definitely an option, but using scripts to generate scripts is not always an elegant solution.  The embedded code is hard to read, editors don't readily identify the code, and you expose yourself to two layers of script debugging.

---

### Post by euler_fan on 2007-08-15
> **meatpan said:**
> That is definitely an option, but using scripts to generate scripts is not always an elegant solution.  The embedded code is hard to read, editors don't readily identify the code, and you expose yourself to two layers of script debugging.

Thanks, I'll bear that in mind.

At this point I would mostly be using it to iteratively run the same script over and over again dumping the results as a set of text files to a specified folder. I have an algorithm to benchmark and the algorithm is implemented as part of a custom R function whose arguments contain all the necessary options and other information.

Would that be a good use of Perl or Bash scripts?

---

### Post by meatpan on 2007-08-16
> **euler_fan said:**
> Thanks, I'll bear that in mind.

At this point I would mostly be using it to iteratively run the same script over and over again dumping the results as a set of text files to a specified folder. I have an algorithm to benchmark and the algorithm is implemented as part of a custom R function whose arguments contain all the necessary options and other information.

Would that be a good use of Perl or Bash scripts?

The code below is the typical layout of a script I use to repeatedly call R.  There is essentially a loop that iterates over a set of simulation params, and within the loop are three components.  First, I generate the specific iteration's data files and save them as a common name (this is so I only need to specify one file name in myscript.R).  Second, R is run with various params, processing the commands in myscript.R from a redirected stdin.  In the last step, the R output is switched back to the appropriate simulation iteration identifier.  

Example:

```

#!/bin/bash

params="a b c d"

for param in params; do
  #......generate tmp.Rinput using param....
  ...
  cp file.$param tmp.RInput
  R --silent --vanilla < myscript.R
  mv rfigure.png $param-results.png
  mv rout.txt $param-results.txt
done


```

I think the benefit of this model is that it allows the R script to be relatively compact and generic with the handling of simulation params.  The consequence is the clunky renaming before and after the call to R.

I've never been too pleased with this technique, and I'm always looking for ways to improve scripts.  If you come across anything better, or have ideas for improvement, please let me know!

---

### Post by euler_fan on 2007-08-16
> **meatpan said:**
> The code below is the typical layout of a script I use to repeatedly call R.  There is essentially a loop that iterates over a set of simulation params, and within the loop are three components.  First, I generate the specific iteration's data files and save them as a common name (this is so I only need to specify one file name in myscript.R).  Second, R is run with various params, processing the commands in myscript.R from a redirected stdin.  In the last step, the R output is switched back to the appropriate simulation iteration identifier.  

Example:

```

#!/bin/bash

params="a b c d"

for param in params; do
  #......generate tmp.Rinput using param....
  ...
  cp file.$param tmp.RInput
  R --silent --vanilla < myscript.R
  mv rfigure.png $param-results.png
  mv rout.txt $param-results.txt
done


```

I think the benefit of this model is that it allows the R script to be relatively compact and generic with the handling of simulation params.  The consequence is the clunky renaming before and after the call to R.

I've never been too pleased with this technique, and I'm always looking for ways to improve scripts.  If you come across anything better, or have ideas for improvement, please let me know!

Thanks for that. I'll definately take a look at it and also at some point basic bash scripting to see if I can find a more elegant solution.

<Smacks forehead>

I can't believe I just thought of this for the first time . . . 

Of course, one way to do it is to make all of your scripts inside of a R function with a looping option like this:

```
myscriptfunction<-function(option1,option2, . . . ,loop=1){
for(i in 1:loop){
     #all the other work your script is supposed to do
     . . . 
     #a return statement with all the correct outputs you wanted.
     }
#a return statement with all the correct outputs you wanted.
}

```

That would let you iterate through a script multiple times. Then so long as the individual "sub-scripts"(?) are debugged, you should be able to chain them together. In my case, if I want to test my algorithm on many different simulated datasets, I could do this:

```
simulator1<-function(option1,option2,loop=1){
#load my various needed scripts
for(i in 1:loop){
     #call to data generation script
     #call to analysis script #1
     #foo
     . . . 
     #collect some data about the run
     }
#process data from the various runs
#a return statement with all the correct outputs you wanted.
}

```

Then from within R I could just call the simulator1 function with the options set right to generate as many simulated analyses as I want.

I'm just not sure how scalable that is to, say, running the scripts over a set of datasets stored as .csv files in some folder. It should work though for well-defined problems. But it is also very inflexible.most of it would have to be re-written for each different problem.

What do you think?

---

### Post by sgsong on 2008-01-16
I invoke Rcmdr from an ESS command line. That way, I have the best of both world: powerful editing capability and some simple GUI facilities to view the data structure. This has been working well for me.

---

