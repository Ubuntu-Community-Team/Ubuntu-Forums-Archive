---
title: "Aliases???"
date: 2010-05-16
forum: Desktop Environments
---

### Post by Smokabowl on 2010-05-16
So I checked the /etc/bash.bashrc file and it doesn't have the
 > if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi 

i expected it to. So I checked the The /usr/share/base-files, and there it is. Problem is, it isn't part of the system wide bash, or is it? How do I activate the bash_aliases in Lucid Lynx?

Quick un-related question. Is ./ = /.??

---

### Post by DangerOnTheRanger on 2010-05-16
I'd think you'd just add that code to your .bashrc file.
As for your other question, no, ./ does *not *equal /. .

**./ **means the current directory.
**/. **means the root folder(/).

---

### Post by Smokabowl on 2010-05-16
> **DangerOnTheRanger said:**
> I'd think you'd just add that code to your .bashrc file.
As for your other question, no, ./ does *not *equal /. .

**./ **means the current directory.
**/. **means the root folder(/).Thanks brother

---

