---
title: "Gnome-Terminal prompt problems"
date: 2009-02-08
forum: Desktop Environments
---

### Post by Maverick321 on 2009-02-08
I am having an issue with the bash prompt inside of gnome-terminal.
It appears to be adding my user name to the front of the prompt when Its not suppose to.

This is what appears
```
lex.hoffman@notebook-linux: ~[HOMENET\alex.hoffman@notebook-linux][02:18]~ $
```

This is what it should be
```
[HOMENET\alex.hoffman@notebook-linux][02:18]~ $
```

This is a domain user that is being authenticated with likewise-open. 

This is what i have $PS1 set to in the .bashrc file
```
[\u@\h][\[\033[1;34m\]\[$(date +%I:%M)\]\[\033[0m\]]\[\033[1;31m\]\w\[\033[0m\] $
```

and when I do echo $PS1 from the terminal i get 
```
[\u@\h][\[\033[1;34m\]\[$(date +%I:%M)\]\[\033[0m\]]\[\033[1;31m\]\w\[\033[0m\] $ 
```

So from what I can tell it is being set right and something is wrong with the terminal. Any ideas?

---

### Post by Maverick321 on 2009-02-10
No one has even one idea?

---

### Post by jonlemur on 2009-02-10
The only thing that I can think of is if PROMPT_COMMAND is set to something that would display your username and computer name.  This command is run before each command prompt is displayed, so it could prefix each prompt with what you're getting.  Try ```
echo $PROMPT_COMMAND
``` and see if there's anything there.

---

### Post by Maverick321 on 2009-02-22
> **jonlemur said:**
> The only thing that I can think of is if PROMPT_COMMAND is set to something that would display your username and computer name.  This command is run before each command prompt is displayed, so it could prefix each prompt with what you're getting.  Try ```
echo $PROMPT_COMMAND
``` and see if there's anything there.

Thanks for your response, and your guess was correct
```

echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"

```
is the contents of $PROMPT_COMMAND

Although now the problem is finding where that is being set.

---

### Post by jonlemur on 2009-02-22
This should fix it```
echo PROMPT_COMMAND=\"\" >> ~/.bashrc
``` and restart the terminal, or search through the .bashrc and any other shell configuration files to see if PROMPT_COMMAND is being set there and delete it.  The above code should clear PROMPT_COMMAND at the end of the initialization of bash, so any previous declarations of PROMPT_COMMAND would be overwritten.

---

