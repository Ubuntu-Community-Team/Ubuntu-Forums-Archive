---
title: "STRObe LIght!...dance party!"
date: 2009-02-02
forum: General Help
---

### Post by vaughnm on 2009-02-02
Ok, so I wanna host kick-*** D&B dance parties!
I got it all hooked up and ready to jam...only one problem....no strobe light! 
Although, I found a program called Strobe Light 1.0 that I downloaded. 
I got it from softpedia.com and got the .tar.bz2 file. 
Now here's the problem. I extracted and there IS what seems to be an executable file, simply called strobelight.
I try opening it with the autorun ability only to realize that that isn't how I'm suppose to run it. 
I kinda suck at get these programs up and running from open source websites. I just don't know how/what to do. 
Is there a way to get this program through the terminal or should I be trying to open using a different application.

Help me resolve my issue and you are informally invited to the Katimavik house in Welland Ontario! 

sorry no E.... but there's plenty of fresh bread and popcorn :popcorn:

---

### Post by tad1073 on 2009-02-02
open a terminal and try this
```

cd ~/Desktop/name_of_folder
./configure
make
make check
sudo make install

```

---

### Post by vaughnm on 2009-02-02
nope :(

---

### Post by Crafty Kisses on 2009-02-02
What type of file is it?

---

### Post by vaughnm on 2009-02-02
application/octet-stream? does that mean anything?

properties just say "type:program"

here's the results from the last post-

-when I put in this code-

cd ~/Desktop/name_of_folder
./configure
make
make check
sudo make install

:I get this:

vaughn@vaughn-laptop:~$ cd ~/Desktop/name_of_folder
bash: cd: /home/vaughn/Desktop/name_of_folder: No such file or directory
vaughn@vaughn-laptop:~$ ./configure
bash: ./configure: No such file or directory
vaughn@vaughn-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
vaughn@vaughn-laptop:~$ make check
make: *** No rule to make target `check'.  Stop.
vaughn@vaughn-laptop:~$ sudo make install
sudo: unable to resolve host vaughn-laptop
make: *** No rule to make target `install'.  Stop.
vaughn@vaughn-laptop:~$ 
vaughn@vaughn-laptop:~$

---

### Post by bukwirm on 2009-02-02
By "cd name_of_folder", tad1073 meant that you should cd to the folder containing Strobelight, which appears to be called "StrobeLight" in this case.

The rest of the instructions won't work, by the way. It appears that you need a [Gambas]("http://gambas.sourceforge.net/") interpreter - try the package gambas2. Then should be able to just run the program.

EDIT: Actually, it appears that you need Gambas 1.0 - and it doesn't appear to be in the repositories :(

[This]("http://gambasrad.org/software/gambas-1.x") might work. There should be instructions for compiling it in a file called README or something similar.

---

### Post by vaughnm on 2009-02-02
Wow, I really have no Idea how to do this. I downloaded this gambas app but I don't know how to use. 
I can't seem to open strobelight with it either. What's going on? 
And how do I fix this so I can get my dance on?

---

### Post by vaughnm on 2009-02-02
Ok well now, I uninstalled gambas2. 
so I click on the link to get gambas1 and the link on sourceforge seems to be dead.
Isn't there an easier way to get this app running without having to use gambas? It seems like I will have to "make" the program. 
Sorry I'm being such a noob but this is all new to me. 
So from the beginning...whats my next step?

---

### Post by vaughnm on 2009-02-02
anyone else?

---

### Post by vaughnm on 2009-02-03
Common, somebody's gotta have some sort of idea!

---

### Post by bukwirm on 2009-02-04
It appears that you're probably out of luck with that particular program. You could try [this]("http://www.bobshowto.com/fun/strobe-light.htm") instead.

In response to your other questions:

Yes, you do require Gambas to run StrobeLight. I figured that out by trying to run the executable file (typing ./strobelight in a terminal), which gives the response "bash: ./strobelight: /usr/bin/gbx: bad interpreter: No such file or directory". From a little web searching, gbx is the Gambas 1.0 interpreter.

Make is a program used to control the compilation of software, mostly software written in C and C++. [This page]("http://www.gnu.org/software/make/") has more information on make.

---

### Post by blazemore on 2009-02-04
It's not source, it's an executable...

just run 
```
./strobelight
``` in the folder in which the executable is.

---

### Post by bukwirm on 2009-02-04
blazemore, did that work for you? When I tried, it complained about not being able to find /usr/bin/gbx and quit.

---

### Post by vaughnm on 2009-03-03
Hey thanks. I couldn't strobelight to work but that website was a good find. THanks for the help. 
If you ever DO figure it out let me know.

---

