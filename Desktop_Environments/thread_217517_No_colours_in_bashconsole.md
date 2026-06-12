---
title: "No colours in bash/console"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Barbelos on 2006-07-17
I have a small problem with bash, where all output is in the same colour. It means for example that running the 'ls' command will show all sorts of files and directories in the same colour, and this makes it a bit harder to see what's what.
It doesn't matter if I use konsole, the gnome terminal or anything else. 

The colours were always there by default in previous distros I have tried, but not in Kubuntu it seems. How do I get the handy colours to work?

---

### Post by kabus on 2006-07-17
Does this command give you coloured output? If so I'd suggest creating an alias in your ~/.bashrc.

```
ls --color=auto
```

---

### Post by mogliii on 2006-07-17
Hi,

I occupied myself a while with that. Because I wanted a nice prompt that changes the color depending if I am root.

Just general:
There are two config files that control the look of your bash

1) /etc/bash.bashrc 
Its the global config file and is used first to set everything

2) ~/.bashrc
Its your local file, and is applied AFTER the global one. This means that the local can overwrite every setting set by the global one

To activate the colors in bash, just open your local .bashrc and look for some commented lines. It should already be available.

There is also a nice recource for colours:
[http://www.linuxjournal.com/articles/3215]("http://www.linuxjournal.com/article/3215")

*************************************
For me it looks like this:

in .bashrc I have for the prompt:
```
if [ "`id -u`" -eq 0 ]; then
        PS1='\[\033[31;1m\][root@\h:\[\033[34;1m\]\w\[\033[31;1m\]]\[\033[37;1m\]# \[\033[0m\]'
else
        PS1='\[\033[37;1m\][\[\033[32;1m\]\u@\h\[\033[37;1m\]:\[\033[34;1m\]\w\[\033[37;1m\]]\[\033[0m\]$ '
fi
```
This changes the color depening if I am root (with su) or not

And for the ls command:
```
alias ls='ls --color=auto'
```
Its an alias, that means that every ls is substitued by ls --color=auto


Hope that works

---

### Post by mogliii on 2006-07-17
This might cover all further questions :)

[Bash-Prompt-HOWTO]("http://tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html")

---

### Post by Barbelos on 2006-07-17
Thanks, adding the alias fixed it.
Strange that it's not enabled by default though...

EDIT: Figured out why. I had my old /home directory from SUSE, and this is probably why kubuntu neglected to give me my own .baschrc file. Otherwise it would have been enabled.
There's one in the /root folder which I have copied over to my user now though.

---

