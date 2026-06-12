---
title: "How do I reload .bashrc without logging out?"
date: 2009-01-15
forum: General Help
---

### Post by cb34 on 2009-01-15
Hi, i'm just wondering if there's a way to reload .bashrc real quick without logging out, or even the main bashrc file, for adding aliases and applying them on the fly and things like that??

Thanks to anybody who has some trick for this. :)

lol edit-> right after i hit submit post, i'm thinkin.. do i just have to run the .bashrc script again?.:p:p

---

### Post by 5BallJuggler on 2009-01-15
try this

open a terminal window and type :-

sudo bashrc restart

---

### Post by cb34 on 2009-01-15
with or without sudo.. bashrc: command not found

but thanks for trying.. :)

---

### Post by cb34 on 2009-01-15
i added an alias in /home/cb34/.bashrc for testing purposes..
i cant run: sh .bashrc  or with sudo, without getting an error and it doesn't work..

but when i run: sh /root/.bashrc or with sudo
it runs just fine.. no errors.. and the alias i put in my home .bashrc only works in a root shell.. not for me in regular terminal... weird.... if you can understand what i just wrote.. LOL:p

---

### Post by ajcham on 2009-01-15
```
. .bashrc
```

---

### Post by theozzlives on 2009-01-15
> **ajcham said:**
> ```
. .bashrc
```

```
..bashrc
```

---

### Post by ajcham on 2009-01-15
> **theozzlives said:**
> ```
..bashrc
```

No, that won't work.  The command I gave was correct.

---

### Post by KeyserSoze93 on 2009-01-15
> **theozzlives said:**
> ```
..bashrc
```

No, the first one was right (. .bashrc), assuming your in your home folder, otherwise:
```
. ~/.bashrc
```

A "." on it's own means source a script file, and .bashrc is the name of that files (works even if it's not chmod'ed +x)

Another way, which might be better, is simply to run ```
bash
``` from your existing shell, which will start a new subshell, reading any new changes to bashrc. When you exit that shell, you'll be back at the first shell you opened.

---

### Post by cb34 on 2009-01-15
..bashrc does not work.

. .bashrc when in the home dir and

. ~/.bashrc both do work.. Thank You! (and now i do understand why sh didn't work and this does! Thanks.)

running just... bash ..also works. (i tried.. bash start ..before.. i was so close.LoL :P)

thank you so much guyz!!

:guitar:

---

### Post by mixmaster on 2009-01-15
. .bashrc should work (note the space) but only if you are already in your home directory.

. ~/.bashrc should work anywhere.  

Just bash will work but means that you have spawned an extra command shell.  Not significant unless you do it a lot without exiting the shell on a machine you don't reboot very often

---

### Post by cb34 on 2009-01-17
thanks for the info mixmaster, much appreciated. :)

---

### Post by cb34 on 2009-01-17
why can i not say thank you to anyone in here, nor can i mark this thread as solved.. weird... ??

---

### Post by overdrank on 2009-01-17
> **cb34 said:**
> why can i not say thank you to anyone in here, nor can i mark this thread as solved.. weird... ??
The feature has been disabled for a bit. 
[Here]("http://ubuntuforums.org/showthread.php?t=1039481")

---

### Post by kevdog on 2009-01-17
I always thought the command to use was source, such as

source ~/.bashrc

Is this incorrect?

---

### Post by ajcham on 2009-01-17
> **kevdog said:**
> I always thought the command to use was source, such as

source ~/.bashrc

Is this incorrect?

No, you are correct. '**source**' and '**.**' are equivalent to one another - [see here.]("http://www.ss64.com/bash/period.html")

---

### Post by kevdog on 2009-01-18
Thanks for that tip -- I didnt know they were equivalent -- maybe its just easier for me to remember the name of a command rather than .  Using a . sometimes makes for messy syntax if using this in a script.

---

### Post by Sailo on 2010-03-01
The easiest way to reload bashrc is to run the command

**source .bashrc** (assuming your in your home directory) otherwise put in the complete path ie.   **source ~/.bashrc**

Just remember you'll have to do this for all open terminal windows, as they will have already read the bashrc file when they first opened.

---

