---
title: "profile"
date: 2005-12-26
forum: General Help
---

### Post by rensu on 2005-12-26
Anyone know why my bash_prompt isn't chaning his aspect. I changed some things in /etc/profile but it still don't want to change the prompt.

---

### Post by briancurtin on 2005-12-26
what things have you changed specifically, and have you closed/reopened the terminal after making those changes?

have you changed your PS1 variable to display a different prompt? if so, what do you have it set to?

---

### Post by zoiks on 2005-12-26
This link may be useful.

[http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/)

---

### Post by kabus on 2005-12-26
You have to source the file to get the new settings to work.
But I think the prompt settings in /etc/profile will get overridden by those in your ~/.bashrc anyway.
So change your prompt in ~/.bashrc and then do :

```
source  ~/.bashrc
```

or just

```
. ~/.bashrc
```

---

### Post by kabus on 2005-12-26
Btw, here's a great How-To for customizing your prompt :

[http://www.gilesorr.com/bashprompt/howto/book1.html](http://www.gilesorr.com/bashprompt/howto/book1.html)

---

### Post by briancurtin on 2005-12-26
[QUOTE=kabus]But I think the prompt settings in /etc/profile will get overridden by those in your ~/.bashrc anyway.[/QUOTE]
/etc/profile is the first profile file checked, and isnt overridden by bashrc or bash_profile

---

### Post by kabus on 2005-12-26
[QUOTE=briancurtin]/etc/profile is the first profile file checked, and isnt overridden by bashrc or bash_profile[/QUOTE]

Not directly, you're right.

But after /etc/profile is read bash wil look for ~/.bash_profile and execute its commands if it exists. 
I just took a look at ~/.bash_profile and it sources ~/.bashrc, if it exists.
So the PS1 settings in /etc/profile will be overwritten by the PS1 settings in ~/.bashrc and that's why it is better to change the prompt there.

--------------------------------------------

slightly offtopic :

The following is an excerpt from man bash that explains which files bash reads on startup.
Could someone please explain the difference between an interactive shell and an interactive login shell ?
The definitions in the manual are over my head.

> 
 The following paragraphs describe how bash executes its startup files.  If any of the files exist but cannot be read, bash reports an
       error.  Tildes are expanded in file names as described below under Tilde Expansion in the EXPANSION section.

       When  bash  is  invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and exe-
       cutes commands from the  file  /etc/profile,  if  that  file  exists.   After  reading  that  file,  it  looks  for  ~/.bash_profile,
       ~/.bash_login,  and  ~/.profile,  in that order, and reads and executes commands from the first one that exists and is readable.  The
       --noprofile option may be used when the shell is started to inhibit this behavior.

       When a login shell exits, bash reads and executes commands from the file ~/.bash_logout, if it exists.

       When an interactive shell that is not a login shell is started, bash reads and executes commands from ~/.bashrc, if that file exists.
       This  may  be  inhibited by using the --norc option.  The --rcfile file option will force bash to read and execute commands from file
       instead of ~/.bashrc.


---

### Post by rensu on 2005-12-27
But if i want to put the prompt for everyone?

---

