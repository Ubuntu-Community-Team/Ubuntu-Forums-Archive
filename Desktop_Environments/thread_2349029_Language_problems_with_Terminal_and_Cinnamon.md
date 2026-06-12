---
title: "Language problems with Terminal and Cinnamon"
date: 2017-01-10
forum: Desktop Environments
---

### Post by DifferentTrains on 2017-01-10
Hi everyone,
I have my locale (so time, date, etc) set to UK, but would like to use Esperanto as my language on the desktop. After switching language on the system (Ubuntu 64 bit running Cinnamon), I found terminal no longer worked. I could get around this by installing and using xterm, which still worked fine. 

I later reinstalled setting the language to Esperanto during install and so everything was set to that to start with (but with locale the same). However I find the default Terminal application still doesn't work, and I have to use xterm. There are a few other things which seem to be defaulting now to English which were in Esperanto after switching languages earlier (such as days of the week in English, Menu instead of Menuo, All applicatons instead of Tutaj programoj or something similar, etc).

Any idea how to sort this?

---

### Post by sudodus on 2017-01-10
This is a workaround: Do you know, that you can ***tweak xterm*** so that it looks pretty nice? For example

```
xterm -title 'xt - my own xterm' -fa default -fs 10 -bg '#2b2c2b' -fg '#f0f0f0' -sb -rightbar
```

according to the manual ```
man xterm
```

You can make an alias for it, for example ***xt***,

```
alias xt="xterm -title 'xt - my own xterm' -fa default -fs 10 -bg '#2b2c2b' -fg '#f0f0f0' -sb -rightbar"
```

and add it near the other aliases in **~/.bashrc**

The next time you start a terminal window, you will have the alias ***xt***. You can also make a desktop file with the tweaked xterm command line, after Exec=

-o-

I don't know how to fix the problem with the standard terminal window and Esperanto, I hope somebody else can help you with the problem itself.

---

### Post by DifferentTrains on 2017-01-12
I found a solution, which I am sharing here for anyone else having similar problems.
Open a hidden folder in your home directory called ".pam_environment". Control+h to show hidden files, or for those who prefer a terminal, your favourite text editor followed by ~/.pam_environment.
Add these two lines (or alter them if already there):
```

LANG=eo
LANGUAGE=eo

```

I put eo for esperanto, but of course change to whichever language you wish to use.

---

### Post by sudodus on 2017-01-12
Thanks for sharing your solution :-)

---

