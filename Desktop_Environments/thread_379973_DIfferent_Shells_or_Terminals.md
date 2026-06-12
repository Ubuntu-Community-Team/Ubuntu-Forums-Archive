---
title: "DIfferent Shells or Terminals?"
date: 2007-03-09
forum: Desktop Environments
---

### Post by freebird54 on 2007-03-09
I think I will be living in two worlds on Ubuntu, command line and Beryl!  Now the Beryl thing will only require patience - and more than I can think of WILL appear.  However, I have used lots of  CLI's, and I miss some things from the best ones.  It may be that there is a shell with the 'missing' features, or *I* may be missing them in bash.

Can you:
1: Display the path (maybe reversed text colours) at the top of the terminal window? Or even the title bar?
2: Print elapsed time for the previous command's execution in the prompt?
3: Have any keystroke pause screen output, so you can enter a further command, and then resume output on <enter> ?  (great for instant scripts - give it a few commands to chew on, then come back later to see how it did)  Also means **more** is needed **less** :D
4: does command completion look in current session history, then overall history before defaulting to 'the usual'?

You get the idea :)

OR - do I have to get good enough to write my own??

Thanks - if anyone knows what I'm talking about.....

---

### Post by Crooksey on 2007-03-09
1: Display the path (maybe reversed text colours) at the top of the terminal window? Or even the title bar?
2: Print elapsed time for the previous command's execution in the prompt?
3: Have any keystroke pause screen output, so you can enter a further command, and then resume output on <enter> ? (great for instant scripts - give it a few commands to chew on, then come back later to see how it did) Also means more is needed less
4: does command completion look in current session history, then overall history before defaulting to 'the usual'?

1. Yes, this is called a dynamically set title ( i think), I cant remember but I think its supported in gnome-terminal and rxvt-unicode.
2. Yes thats easy, use your favorite text editor and open up your ~/.bashrc file, if you want a colour prompt, make it look like....

```

BLACK='\e[0;30m'
BLUE='\e[0;34m'
GREEN='\e[0;32m'
CYAN='\e[0;36m'
RED='\e[0;31m'
PURPLE='\e[0;35m'
BROWN='\e[0;33m'
LIGHTGRAY='\e[0;37m'
DARKGRAY='\e[1;30m'
LIGHTBLUE='\e[1;34m'
LIGHTGREEN='\e[1;32m'
LIGHTCYAN='\e[1;36m'
LIGHTRED='\e[1;31m'
LIGHTPURPLE='\e[1;35m'
YELLOW='\e[1;33m'
WHITE='\e[1;37m'
NC='\e[0m'  

PS1="\[$LIGHTGREEN\]\u@\h \[$YELLOW\]\@ \[$LIGHTBLUE\]\w \$ \[$NC\]"

```

Thats going to be your current prompt, but colorful and with a time stamp.

example - [http://phil0d0x.com/bashrc.png](http://phil0d0x.com/bashrc.png)

3. Do you mean like run the "ls" command and only show certain results?...

```

ls | grep <what you want to show>

```

4. Just default, not sure if it checks recently used commands....

When im editing sources.list It always asks me whether i want apt or apm ;P

---

### Post by freebird54 on 2007-03-09
I was pretty sure bash was colourful, but I am glad to learn that the path in the titlebar trick might be out there somewhere.

Number 2 is a bit trickier - I like to know that the program/command I just ran takes 0.02 ms or whatever.  I am sure it was on the timesharing machines, and probably the VAXes as well.  I also used it a lot when assembly programming to test 'improvements' in my code :D

The 'any key' pause was always a bit unlikely - I've only ever seen that in 1 CLI (AmigaDOS) - but you could essentially write a script on the fly without leaving the command line, or having to save or execute it.  For instance, I could use the list command recursively throughout the entire machine to list all, say, mp3's, redirect that to a file, then add a mv command that file and gather them all together in a new directory created on the fly - without editing anything, or waiting for the first command to complete.  It was fun at the time! (especially if someone was watching)  :biggrin:

The command completion I will just have to learn here - and see what it does and whether it's useful or not - some aren't (they know more than I do!)


Thanks for the response - I can go looking with more focus on what can be found now I guess!

BTW  - can the prompt execute a command?  I could probably write my own assembly 'widget' to dump the time into the prompt if it will execute anything......

Love that Ubuntu (and Penguins, of course)

---

### Post by Crooksey on 2007-03-09
I don't 100% understand your questions, but everything relating to prompt customization relies in ~/.Xdefaults and ~/.bashrc, google around to get more info.

---

### Post by olejorgen on 2007-07-04
2:
```

time <command>

```

---

