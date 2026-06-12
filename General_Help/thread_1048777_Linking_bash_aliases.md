---
title: "Linking bash aliases"
date: 2009-01-23
forum: General Help
---

### Post by steve228 on 2009-01-23
Recently, I created some aliases in my .bashrc file and I am wanting to create a separate .bash_aliases file.  How can I get my .bashrc to recognize the alias file?

Thanks for the support

---

### Post by Joeb454 on 2009-01-23
Remove the aliases from your .bashrc and add them to ~/.bash_aliases (if you haven't already).

Then look for this part of your .bashrc ```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

The if statement will probably be commented out (with a # at the beginning of the line).

Remove the #'s so it looks like the above, and they should then work :)

---

### Post by steve228 on 2009-01-27
Very helpful and easy to understand...

This worked great Thank you so much... is there a certain way to mark the thread as solved?

---

### Post by cdtech on 2009-01-27
Here is a thread on .bash_aliases that may be interesting for ya.....
[http://ubuntuforums.org/showthread.php?t=616875&highlight=bash_aliases](http://ubuntuforums.org/showthread.php?t=616875&highlight=bash_aliases)

---

### Post by adamlau on 2009-01-27
Thanks for the link, I added a few aliases of my own :) .

---

