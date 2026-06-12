---
title: "readability formulas"
date: 2010-05-16
forum: Education &amp; Science
---

### Post by MCBaker on 2010-05-16
Is there a program for running readability statistics available?  I am thinking of Flesch-Kinkaid reading level, or Flesch Reading Ease Scale.  It would be relatively easy to arrive at an algorithm for samples of text, based on length of words, length of sentences, complexity of clauses, frequency of use of words, etc.  You would need to do some research on existing formulas.

---

### Post by radioboy on 2010-05-16
A quick google search of:  linux "Flesch-Kinkaid"
gave me this as a first result [http://flesh.sourceforge.net/]("http://flesh.sourceforge.net/")
:tongue:
It also has a [manual]("http://flex.sourceforge.net/manual/"), and a command line version.
It's written in Java. I tried it with a pdf document and it worked well, or well, it did't crash and got me a couple of numbers. :)

I hope this is what you are looking for!

---

### Post by MCBaker on 2010-05-16
Cool.  However, I have difficulty unpacking zipped files.  Java is what I need.  Is that in package managers, or what?  I am just a beginner with this.

Also, is there a calculator which runs standard deviation and correlation coefficients?  Statistics.  I really don't want to use the equivalent of SPSS yet.

---

### Post by radioboy on 2010-05-16
Ubuntu  includes by default an archive manager, so it's only a few clicks away. With right click over the .zip file you will be presented with a context menu with an option to extract it. Regarding java, read this...
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Sun%20Java%20moved%20to%20the%20Partner%20repository]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Sun%20Java%20moved%20to%20the%20Partner%20repository")
...and this:
[http://ubuntuforums.org/showthread.php?p=9040217]("http://ubuntuforums.org/showthread.php?p=9040217")
You need the Java JRE package (sun-java6-jre), in case you don't want to install OpenJDK. It will install the dependencies, so no worries. :)

---

### Post by radioboy on 2010-05-16
Regarding a calculator, I don't know, because I usually do all that in Python.
You might try using OpenOffice Calc, for example.

And well, when you need an SPSS equivalent, you have R.

You can do it as well with Python if you use the package [Numpy]("http://www.scipy.org/Numpy_Example_List_With_Doc#head-f08a3e6b178e230a18c172bbbe4c755f799a803f") and/or Scipy. (And iPython is a very good addition for auto-completion and other nice tricks.)
See also this:
[http://www.scipy.org/Cookbook/LinearRegression]("http://www.scipy.org/Cookbook/LinearRegression").

Surely there are other methods, but I've not needed to look for anything else.

---

### Post by MCBaker on 2010-05-16
I think I need to get deeper into Ubuntu Pocket Guide before I go any further.  Thanks.

---

### Post by MCBaker on 2010-05-16
Yes, spreadsheet gives you the ability to enter data, then apply formulas.  More like SPSS applications than a stat calculator.  Actually better in the case of paired data like pre-test and post-test or correlation.

---

### Post by radioboy on 2010-05-16
Oh, well. Somehow I had the idea of SPSS being more R-like.
Gnumeric also has a good and easy to use set of statistical tools. After selecting a pair of data columns (x,y) and applying linear regression over them from the menu (Tools -> Statistical analysis -> Regression), you can get a very detailed numerical summary of the procedure on a separate sheet.

---

### Post by MCBaker on 2010-05-16
Whoah!  I'm just getting my bearings with the potential of Ubuntu itself.  <grin>  Gotta do this step-by step.

---

### Post by MCBaker on 2010-05-16
No, that is not the kind of program I want for readability measures. 

[http://www.readabilityformulas.com/flesch-reading-ease-readability-formula.php](http://www.readabilityformulas.com/flesch-reading-ease-readability-formula.php)

This is the $$$ one.

---

### Post by radioboy on 2010-05-17
What about this?

*Improve your writing with the GNU style checkers*
[http://www.linux.com/archive/feed/56833]("http://www.linux.com/archive/feed/56833")

They are command line programs (this is, they are "CLI" programs, for Command-Line Interface, a concept you will likely find often) and are executed in the console, but some GUI could be used/built for them, and you can use other commands for conversion of formats to get the text.
For example, [FONT="Courier New"]antiword[/FONT] reads .doc files, and they can be "fed" as simple text to these analysis programs to get your results.
Other programs also exist to convert pdf to text, odt to text, etc.

Let us know how is it going! :)

---

### Post by MCBaker on 2010-05-17
Yeah, that's what I want :P So it is not in a depository, therefore the correct dependencies are not attached, so I can't use it until those in the know get it fixed up for Ubuntu?  Given I'm just a beginner, I really don't want to foul things up with some serious mistakes.

---

### Post by radioboy on 2010-05-17
No worries, the 'style' and 'diction' commands come together in the diction package. You just have to open Synaptic Package Manager and search for 'diction'. Then you can use it in the command line.
Another option is to install it from the command line, like this:

[FONT="Courier New"]sudo apt-get install diction[/FONT]

This will ask for your password to authorize the installation.
(You might want to read about sudo and how to use it properly.)

Be aware that in the web page where examples of these commands are shown, they use "Doubled word" instead of "Double word". The last is the correct one. (Maybe product of some posterior change, the article is from 2006).

While writing this, I found a tool for OpenOffice, but for some reason is not working for me:
[http://extensions.services.openoffice.org/project/languagetool](http://extensions.services.openoffice.org/project/languagetool)
[http://www.languagetool.org/screenshots/](http://www.languagetool.org/screenshots/)

Anyway, if you stick to the CLI version, you will need to learn a few extra commands, like 'echo', 'cat', redirection operators like '>' and '>>', pipes '|', and 'grep', for example.
I suggest you reading some introductory guide to the Linux shell:
[http://gd.tuwien.ac.at/linuxcommand.org/lts0020.php]("http://gd.tuwien.ac.at/linuxcommand.org/lts0020.php")
[http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php]("http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php")

You can find the manuals for style and diction in the same command line, typing:
[FONT="Courier New"]man style[/FONT]
and
[FONT="Courier New"]man diction[/FONT]
You can navigate the manuals with the arrow keys, page-up and page-down, you can search terms typing a slash '/' (use 'n' and 'N' for next and previous finds) and you exit with 'q'.

See also manuals for printing and viewing here:
[http://www.sunsite.ualberta.ca/Documentation/Gnu/diction-0.7/man/diction.1.html](http://www.sunsite.ualberta.ca/Documentation/Gnu/diction-0.7/man/diction.1.html)
[http://www.sunsite.ualberta.ca/Documentation/Gnu/diction-0.7/man/style.1.html](http://www.sunsite.ualberta.ca/Documentation/Gnu/diction-0.7/man/style.1.html)

...and web interfaces!
[http://www.kcte.org/fun/style.html](http://www.kcte.org/fun/style.html)
[http://www.kcte.org/fun/diction.html](http://www.kcte.org/fun/diction.html)

Let's say that you have a '.doc' file.
You just install "antiword": [FONT="Courier New"]sudo apt-get install antiword[/FONT]
and then, making sure you are in the correct folder:

[FONT="Courier New"]antiword file.doc | style -s | grep "Double word"[/FONT]

So antiword converts the doc file to text, which is passed with a pipe '|' to style, which analyzes with the flag '-s' activated, and the result goes to grep, which selects only those parts of the analysis that include 'Double word'.
And what if I want to pass this result to a text file? Simple:

[FONT="Courier New"]antiword file.doc | style -s | grep "Double word" > result.txt[/FONT]

Also check the commands pdftotext, ps2txt.
Be aware that you will need to use these commands separately, converting first to text and then doing the analysis over the resulting text file. 
Good luck!

---

### Post by MCBaker on 2010-05-17
That looks easy enough for a beginner like me.  Thank you.

---

