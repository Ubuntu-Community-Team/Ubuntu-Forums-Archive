---
title: "Word Count in Texmaker"
date: 2009-04-07
forum: General Help
---

### Post by deathblossom on 2009-04-07
Hey all,

I'm trying to get Texmaker to do a word count of my latex files. I found this perl script here:

[http://wing.comp.nus.edu.sg/~min/texWordCount/](http://wing.comp.nus.edu.sg/~min/texWordCount/)

which does what I want.

The gold standard for me would be if I can press some keys and have the output of this script output to the Messages/Log File section for me. However, while Texmaker will run the command, it won't actually output anything there and simply says process started and exited normally. I assume this is because the command doesn't generate a log file? Is there a way to make Texmaker output the results of this script to that section?

---

### Post by 3Miro on 2009-04-07
Try playing with Texmaker -> User -> Commands.

---

### Post by deathblossom on 2009-04-08
Yeah, I've got a user command set up with the command:

texWordCount.pl %.tex

which when run in the terminal gives me:

1885	whole - dp1report.tex
	158	Section 1 - XXX
	822	Section 2 - XXX
		300	Subsection 1 - XXX
		111	Subsection 2 - XXX 
		168	Subsection 3 - XXX
		207	Subsection 4 - XXX
	354	Section 3 - XXX
	327	Section 4 - XXX
	201	Section 5 - XXX

but when done in Texmaker just gives me:

Process started

Process exited normally.

So I don't know how to get the results output the messages/log file box.

---

### Post by deathblossom on 2009-04-08
I figured it out. I had to find where the perl script was printing the output and append STDERR before it to make Texmaker show it.

---

### Post by Pixilarion on 2009-04-23
Using these instructions, I was able to adapt version 2.1 of the script: it now prints the statistics to texmaker. You just have to add a user-command "/path/to/script/ %.tex"

---

### Post by caitifty on 2010-01-01
Another option: in User -> User commands -> Edit User Commands

In the 'Menu Item' field put: Wordcount  (or whatever you want)
In the 'Command' field put: wc -w %.tex

That's it.  User -> User Commands -> Wordcount now gives you a straight wordcount for the entire open document in the messages pane.

If you want # lines instead of # words change the above to wc -l %.tex.  For other options (# characters, # bytes..) type wc --help on a command line.

I have to admit that I was surprised to find Texmaker/x doesn't have a built-in wordcount utility though.

---

### Post by larsonj on 2010-08-31
> 
In the 'Menu Item' field put: Wordcount  (or whatever you want)
In the 'Command' field put: wc -w %.tex


I tried this, but all I get out is "Process Started" ... "Process Exited Normally".  How to I get the results?

Thanks,
John

---

### Post by nivwusquorum on 2011-04-19
Pixilarion script works just fine, but for some reason, no newlines are passed to message window in texmaker. Any way to fix it? I know a little programming, so it can be just overview of possible solution if somebody don't have time to go deep into problem.

---

### Post by mesolithic on 2012-04-18
sorry to raise this thread from the dead. but i thought someone else might find this useful.

the first script linked in this thread is really good and can jump from tex file to tex file if your latex project has multiple tex files (e.g. one for each chapter).

instead of trying to tweak the script to print to STDERR, i wrapped the entire perl script within a shell script that wrote to a file. After which an xmessage command in texmaker to have a pop-out message showing the breakdown of wordcount without the newline issues mentioned above.

counter.sh:
```
#!/bin/bash
perl texWordCount.pl $1 > count.txt
```


and in texmaker user commands:  
```

sh counter.sh %.tex | xmessage -file count.txt
```

---

### Post by oldos2er on 2012-04-18
Old thread closed.

---

