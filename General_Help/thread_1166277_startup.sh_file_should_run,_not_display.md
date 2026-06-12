---
title: "startup.sh file should run, not display"
date: 2009-05-21
forum: General Help
---

### Post by kvk on 2009-05-21
Hi~

I'm running Kubuntu 8.04, and have a single line in the file

~/.kde/Autostart/startup.sh

which is

source ~/.bashrc


However, on startup, KDE opens the file in Kate and displays it! I don't need to see it, just have it executed. What's the procedure for this?

Thank you!

---

### Post by geirha on 2009-05-21
Even if it had run the startup.sh file, the script itself is pointless, because it would've started a new shell, run the "source ~/.bashrc" in that shell, then the shell is closed, and any variables set by the source command goes with it. What are you trying to do exactly?

---

### Post by kvk on 2009-05-21
I'm running some modeling code inside Emacs, with some configurations written into the .emacs file and some .el files inside the Emacs lisp directory. I need to configure the PATH directly at login so it's possible to compile models from within Emacs, without necessarily opening a shell. Since the .bashrc is only executed within the shell, I set ~/.kde/Autostart/startup.sh:

 #!/bin/bash
 source ~/.bashrc


Should that not remain stable throught the entire login session? Of course, as it's not working, maybe that's my clue right there! :-p

Then within the .bashrc file I have the modified PATH statements that should route everything correctly.

---

### Post by geirha on 2009-05-21
Try setting the PATH in /etc/environment instead.

---

### Post by kvk on 2009-05-21
Dang! Thanks for the suggestion- I was hoping that would work!

But I still get the same error returned within Emacs:

COMMANDFOO

/bin/bash: COMMANDFOO: command not found

For some reason, Emacs isn't detecting the correct PATH routing to the directories where the command definitions are stored. Everything else appears to be working well- all the syntax coding and modified tool bar and such are right on. If I open a shell I can run the commands with no problem.

Of course, it might not be the PATH itself that's the problem, but some other line I have in there that's preventing the routing.

---

### Post by geirha on 2009-05-21
After changing /etc/environment you need to log out and back in again for the change to take effect. Forgot to mention that, sorry.

---

### Post by kvk on 2009-05-23
No worries- I did it automatically. :-)

It didn't work, however, and I'm thinking I should be able to modify whatever I need within my home directory without going into general system files; I must be making an error somewhere else.

Which still doesn't tell me why the silly thing opens in the first place upon log-in! Isn't the startup.sh file simply supposed to execute whatever commands are contained within it as opposed to displaying the file itself? Or am I missing something else in here?

---

### Post by jpkotta on 2009-05-24
You could set the PATH in Emacs itself, although putting it in your ~/.bashrc is better because it will be visible to more programs.  I'm surprised KDE doesn't automatically source your ~/.bashrc already.
```
(setq path-as-list (split-string (getenv "PATH") ":"))
(add-to-list 'path-as-list "/path/to/things")
(setenv "PATH" (mapconcat 'identity path-as-list ":"))
```

---

### Post by kvk on 2009-05-24
Well, that worked! Thanks!

I set the lines:

```

(setq path-as-list (split-string (getenv "PATH") ":"))
(add-to-list 'path-as-list "home/arctos/admb/bin")
(setenv "PATH" (mapconcat 'identity path-as-list ":"))

```

in the .emacs file, and then running

```

M-x getenv
PATH

```

inside Emacs showed the home/arctos/admb/bin present in the PATH string.

I have some additional files called to load from the .emacs file that should also have set this correctly, but as they apparently didn't, I'll need to check and find out why.

I still can't get the commands defined within the admb/bin file to run properly, but at least the correct PATH is there and I can work on from here.

Thank you!!

---

### Post by jpkotta on 2009-05-24
> **kvk said:**
> 
```

(add-to-list 'path-as-list "home/arctos/admb/bin")

```


That should probably be an absolute path, e.g. "/home/arctos/admb/bin".

---

### Post by paradigm2 on 2009-05-24
<removed>

Answer was already given.

---

### Post by kvk on 2009-05-24
Ha!

Dorks'R'Me!

Added the absolute, and some of the commands are functioning now.

Many thanks!!

---

