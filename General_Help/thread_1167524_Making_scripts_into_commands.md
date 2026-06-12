---
title: "Making scripts into commands"
date: 2009-05-23
forum: General Help
---

### Post by Aped on 2009-05-23
Hey folks, like many newish linux users, I have taken a lot of pleasure in turning many oft-repeated actions (certain types of batch moves involving find -exec, for instance, or recursive shreds or batch renames, that sort of thing) into bash scripts for speedy zoomzooming. 

However, I always have to navigate to my /Scripty/ dir in order to execute these scripts -- is there an easy way to make them into 'commands' - eg: 
```
andrew@nubuntu:~$ infomux OldContacts/*.vcf NewContacts.csv
```

I want to be able to do it right from the command line, without navigating or pointing to my obscure scripts folder; is it as simple as adding these files to the /bin/ folder or some registry somewhere? Or do these items actually have to be compiled (sigh, bin *does* stand for binary, right?) C/C++/etc programs?

As usual, thanks in advance for all the help ubuntuforums.

Edit: Yeah, I could add it to aliases in .bashrc now that I really think hard on it, though that seems sort of hack-n-slash. Any *other* (read: proper) ways of doing it?

---

### Post by egalvan on 2009-05-23
I am just as lazy as the next guy (or more so)...

so commands like that, I have made into bash scripts,
placed them in my ~/bin, and made "launchers" on my desktop.

example....

editing grub 

I created a file named
"edit_grub"
which contains this text
```
#!/bin/bash
## open menu.lst
gksudo gedit /boot/grub/menu.lst
```

I placed this file in ~/bin

the launcher on desktop runs

```
/home/ernest/bin/edit_grub
```

as the "command"

then double-clicking on this will fire up gedit with menu.lst...


note:
the comments are for my convenience...
I learned early on to ALWAYS comment my code...
no matter how simple it was...

---

### Post by Locutus_of_Borg on 2009-05-23
```
echo "alias <command_name>='infomux OldContacts/*.vcf NewContacts.csv' >> ~/.bashrc
``` 

then open a new terminal and whatever you put in for <command_name> will execute that 'script'

---

### Post by capscrew on 2009-05-23
> **Locutus_of_Borg said:**
> ```
echo "alias <command_name>='infomux OldContacts/*.vcf NewContacts.csv' >> ~/.bashrc
``` 

then open a new terminal and whatever you put in for <command_name> will execute that 'script'

That will get messy in a short time.  Read the .bashrc file.  There is a section to uncomment that allows you to use a separte file (.bash_aliases) for that kind of thing.

But these are not aliases anyway.  The OP should make sure the ~/bin 
directory is in the current $PATH variable.  This also can be accomplished in the .bashrc.  Look for and uncomment the ~/bin section.

Edit: Shoot, I'm too much of a perfectionist - Here is the **aliases** part of the .bashrc  ```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

And here is the **$PATH** section```
# Add personal bin dir to path

if [ -d ~/bin ] ; then
PATH="${PATH}":~/bin
fi

```

---

