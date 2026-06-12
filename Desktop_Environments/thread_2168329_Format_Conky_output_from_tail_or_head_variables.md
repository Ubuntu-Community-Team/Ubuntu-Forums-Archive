---
title: "Format Conky output from tail or head variables"
date: 2013-08-17
forum: Desktop Environments
---

### Post by demontager on 2013-08-17
I don't have a problem actually, but want to ask about one feature if it exist in Conky.  I'm using Conky variable ${tail} or ${head} to list content of log files. So, for instance I got file with such content:

load: 75
disc: 45
files: 100

And for example ${head} outputs file as is all in one color, but i want to supply ${color} option to digits to be more distinguishable from main text. Is it possible with Conky to do so ?

---

### Post by stinkeye on 2013-08-18
You could use sed to insert color variables.
This works if your output from the log file is always of the form **text: digits**.

eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **cat ~/test.txt**
load: 75
disc: 45
files: 100
```


Then use sed to add **${color}** to the start of each line and replace "**:**" with "**:${color red}**"
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **cat ~/test.txt | sed 's/^/${color}/' | sed 's/:/:${color red}/g'**
${color}load:${color red} 75
${color}disc:${color red} 45
${color}files:${color red} 100
```

Then in conky use the execpi command to parse the inserted variables.
eg 
```
${execpi 300 cat ~/test.txt | sed 's/^/${color}/' | sed 's/:/:${color red}/g'}
```


From man conky....
> **execp command **
 Executes a shell command and displays the output in conky. warning: this takes a lot more resources than other variables. I'd recommend coding wanted behaviour in C and posting a patch. This differs from $exec in that it parses the output of the command, so you can insert things like ${color red}hi!${color} in your script and have it correctly parsed by Conky. Caveats: Conky parses and evaluates the output of $execp every time Conky loops, and then destroys all the objects. If you try to use anything like $execi within an $execp statement, it will functionally run at the same interval that the $execp statement runs, as it is created and destroyed at every interval. 

**execpi interval command **
 Same as execp but with specific interval. Interval can't be less than update_interval in configuration. Note that the output from the $execpi command is still parsed and evaluated at every interval.

---

### Post by demontager on 2013-08-18
That exactly what i wanted to know, awesome! Many many thanks!

---

