---
title: "wanted: shell with better autocompletion"
date: 2007-11-05
forum: Desktop Environments
---

### Post by izak on 2007-11-05
Hi all

I'm looking for a shell with autocompletion on previous commands similar to the ipython shell's (which is only useful playing around with python).

Specifically I want to be able to type in one or more letters of a previous command i had entered and then press up and have the shell cycle through only the commands that start with those letters.
(In bash if you pres up it cycles through ALL your previous commands. Or is there a way to change this behaviour?)

Also an easy way to bookmark folders in the shell would be nice. In ipython you simply type 'bookmark <name>' to have the current location bookmarked. I've emulated this behavour by defining bookmark vairables in my .bashrc but it is a bit more cumbersome...

Thanks!

---

### Post by Slychilde on 2007-11-05
You can do auto completion just fine in bash.  If you type in part of a command or path and then hit the tab key once, it will auto complete if there is only one option that would complete that command; a second tab hit will display a list of all possible commands.

---

### Post by izak on 2007-11-05
No, I'm not talking about normal autocompletion (which works fine), but autocompletion of *previously entered* commands (with all their previously entered options). 

For example if my command history is 

"
ls /home/*
less /home/izak/ foobar.txt
gunzip /home/izak/foobar.tar.gz
grep foobar
"

and I hit the up arrow bash will cycle trough these commands. But what I want is to type "l" and then press up to have the shell cycle through only the top two commands. Or if I press "le" followed by up it should autocomplete "less /home/izak/ foobar.txt". This is a very useful feature I use often in the iPython environment.

Is there a shell that can do this?

---

### Post by YoG%*@ on 2007-11-05
hell-o,

you can use <ctrl> - r to search for a certain command that you previously typed. might be sort of what you're looking for..?

hth,
mux

---

### Post by izak on 2007-11-05
Yes thanks! that works like I want it.

---

### Post by YoG%*@ on 2007-11-05
glad i could help =)

---

### Post by jpkotta on 2007-11-14
I like this functionality bound to the vertical arrows.  So I add the following to my ~/.inputrc:
```

    # non-incremental search of history based on the text between the prompt and the cursor
    # up arrow
    "\e[B": history-search-forward
    # down arrow
    "\e[A": history-search-backward

```

---

