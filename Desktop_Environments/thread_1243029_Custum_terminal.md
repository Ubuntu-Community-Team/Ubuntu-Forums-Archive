---
title: "Custum terminal"
date: 2009-08-17
forum: Desktop Environments
---

### Post by @echo off on 2009-08-17
I hope I posted in the right section.

So i wanted to customize my terminal and so I came up with this:
```

PS1="\e[0;30m.\e[m\e[0;31m/\e[m\e[0;34mTime\e[m\e[0;31m|\e[m \e[0;30m\t\e[m \n \e[0;30m\w\e[m \n\e[0;30m.\e[m\e[0;31m/\e[m\e[0;34mTerminal\e[m\e[0;31m|\e[m\e[0;30m~$\e[m "

```the only problem is, after a certain number of characters are entered in, it goes to the begining of that particular line and over wrights itself. But it still somehow keeps the whole line intact. for example:
If I wand to run: 
```

echo my long sentence

```instead of: 
```

./Terminal|~$ echo my long sentence

```it looks like:
```

tenceminal|~$ echo my long sen 

```If I press backspace to erase what I type, just the 'e' in 'tence' it looks like this:
```

tenc

```What can I do to fix this?

---

### Post by zerhacke on 2009-08-17
Put it in your .bashrc file.

---

### Post by @echo off on 2009-08-17
> **zerhacke said:**
> Put it in your .bashrc file.

put what there? Ih your refering to the:
```

PS1="\e[0;30m.\e[m\e[0;31m/\e[m\e[0;34mTime\e[m\e[0;31m|\e[m \e[0;30m\t\e[m \n \e[0;30m\w\e[m \n\e[0;30m.\e[m\e[0;31m/\e[m\e[0;34mTerminal\e[m\e[0;31m|\e[m\e[0;30m~$\e[m "

```
That is from the .bashrc file. I beleieve it has something to do with line wrapping and non-printing characters. 
[http://drnathan.teamhackaday.com/2009/04/03/fix-your-linux-terminal-line-wrap-issues/](http://drnathan.teamhackaday.com/2009/04/03/fix-your-linux-terminal-line-wrap-issues/)
I did some research, not much but some, and this sounds reasonable. I just dont know where to put the \[ and\]

---

### Post by @echo off on 2009-08-17
Solved it:
```

"\e[0;30m.\e[m\e[0;31m/\e[m\e[0;34mTime\e[m\e[0;31m|\e[m \e[0;30m\t\e[m \n \e[0;30m\w\e[m \n\[\e[0;30m\].\[\e[m\]\[\e[0;31m\]/\[\e[m\]\[\e[0;34m\]Terminal\[\e[m\]\[\e[0;31m\]|\[\e[m\]\[\e[0;30m\]~$\[\e[m\] "

```

To save you time, I put the \[ and \] around the colour settings for the './Terminal|~$' string and that fixed it.

---

