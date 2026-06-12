---
title: "Error 1 on &quot;make&quot;"
date: 2006-01-27
forum: Desktop Environments
---

### Post by Luke771 on 2006-01-27
After playing with Cheops for a while, I wanted to switch to Cheops-ng, so I downloaded it from Sourceforge and tried to install it. For something like 7 hours. Many new installed packages, and many aborts later, was still trying to run ./configure succsessfully.
Then I realized that I could see a list of options running 
```
./configure -help

```
The good news is that now I wont forget easily that I actually *have* an -help option 
The ./config command finally worked without error caused aborts, but I had to disable the last three tests because it keeped aborting on gtktest when it failed to fine some file (GTK *is* installed, but not in the "right" directory), and the same thing happened with glibtest after disabling gtktest, and again with imlibtest, with both gtktest and glibtest disabled; so I typed```

./configure --disable-gtktest --disable-glibtest --disable-imlibtest

```
Next on the installation instructions provided by the Readme file was```

make
make install

```But when I typed "make" in the terminal window I saw a bunch of errors pass thru the window, so when it was done I rolled it back and had a look.
(I'm quoting one of each type skipping "quasi-redundant" messages where all that change is a small detail like a number or something like that. 
> 
types.c:860: warning: pointer targets in passing argument 2 of &#8216;adns__vbuf_appendq&#8217; differ in signedness


> 
query.c:182: warning: pointer targets in passing argument 3 of &#8216;query_simple&#8217; differ in signedness

> 
transmit.c:98: warning: operation on &#8216;p&#8217; may be undefined

> 
check.c:172: warning: implicit declaration of function &#8216;abort&#8217;
check.c:172: warning: incompatible implicit declaration of built-in function &#8216;abort&#8217;


> 
/bin/sh: gnome-config: command not found

> 
event.c:480: warning: pointer targets in passing argument 3 of &#8216;accept&#8217; differ in signedness

> 
event.c:893: warning: unused variable &#8216;hp&#8217;
event.c:892: warning: unused variable &#8216;hostname

> 
/usr/bin/ld: cannot find -lgnomeui
collect2: ld returned 1 exit status
make: *** [cheops-agent] Error 1

The third line from the bottom looks like I need to install gnomeui, which I couldnt fine in Synaptic and apt-get did not find either, but maybe my command line was wrong: I typed only
```

apt-get install gnomeui

```
Without specifying where it should look for the file (by the  way, what was the line, again? I *know* it's not "rtfm" but I could look at some documentation after all)

Questions:
What do those errors mean?
What did I do wrong?
What did I do right? (if any)

and most important:

What should I do next?

---

### Post by Who on 2006-01-27
I am by no means an expert, but when I have similar issues, rather than disabling the checks (as you said you did in ./configure) I make symlinks (simlinks ?) that are in the 'right' place and that link to the real file - it may work...?

---

### Post by Luke771 on 2006-01-27
Cool, I can give that a try. I only need to know what si/ymlinks are and how they are done.
Can you post a quick how-to?
(thanks)

---

### Post by Who on 2006-01-27
A very quick how-to, cos there isn't much how to it ;)

At the command line

```
(sudo) ln -s *source destination*
```

should do the trick. I think that Konqueror can make s?mlinks just by clicking and dragging - Nautilus may be able to aswell
(```
sudo apt-get install konqueror
``` if you want to play (note: this may have a _lot_ of dependencies!)

sudo gains you super user (~=administrator) rights for the command followin it.

```
man ln
``` may help if you need more options

---

### Post by Luke771 on 2006-01-27
hm, maybe I havent really understood what you mean.
of course, "sudo" is one of the first commands you need to learn when you run k/ubuntu, but I was sick and tired of being asked for the password all the time, so I enabled root password and root log-in, and now I  type it in  once,  at log in.

Nautilus does the same things as Konqueror, I guess.

And the $1,000,000 question is:
*what* do I have to put in the place of *source* and *destination*, in the line that you posted?
I havent understood yet what s(y)imlinks are and what they are supposed to link -if- they are actually supposed to link something.

Now, if you have the patience of starting again from the very beginning, I try to summarize what I'm trying to do and where I get to the problem, then I would try to understand what your solution *is*; what should those command lines (or konqueror click-and -drop) do, and which command line does what.

I was trying to ./configure a package called Cheops-ng, I unpacked it in the /usr directory and then I should ./configure it.

After having installed some new packages, it worked *almost* until the end, that is: *almost*; the first problem I could'nt solve was the failed gtktest (disabling tests didnt do the trick, looks like)

So now, as I understand, I should say to ./configure not to look in the directory where it did not find gtk and to look in the directory where gtk is, instead, and I shoud do the same thing about the other two tests, Is that the thing that you are trying to explain?

Cany you try to write something like "this command will do this"
Thank for the help I really appreciate it.

---

### Post by Who on 2006-01-28
Sorry, I normally do try and explain what the commands do - I hate it when people give out commands for me to type and I don't know what they do - I guess you caught me tired or in a hurry ;)

Your last 3 paragraphs are correct. You need to either tell ./configure where to find the packages you believe are installed but that are not recognised by ./configure where they _actually_ are, OR, if that doesn't work you need to make it think they are in the locations it expects by making symlink (google teaches speeling too :P). A symlink, unlike a link on Windows, looks like an actual file, not just a shortcut - you can think of it as just making two 'pointers' on the disk pointing to the same bit of data (the file).

So, to create a symlink you do (well, you do it slightly differently cos you have su but I will use sudo cos it is 'standard' practice around these here parts ;))
sudo ln -s [the place the _actual_ file is] [the place that ./configure expects to see the file]

and ln means make a link, the -s option means make it symbolic.

Now, when you run configure all should work.

**However**
 I looked at the installation instructions here:
[http://cheops-ng.sourceforge.net/download.php](http://cheops-ng.sourceforge.net/download.php)
and it says you need to use gmake

#  untar the file tar -xzvf cheops-ng-X.X.X where the X's represent ther version number
# cd cheops-ng-X.X.X
./configure
**# gmake**
gmake install
# to run: cheops-agent &; cheops-ng just enter the IP address of the machine that you started the server on in the dialog box (cheops-agent will spit out a message "Starting server on X.X.X.X" put the X.X.X.X in the dialog box)

The # means do this at a root command prompt.

Good luck

Who

---

