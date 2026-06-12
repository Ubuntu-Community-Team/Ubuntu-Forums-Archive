---
title: "How to show history (if possible) in terminal"
date: 2009-02-23
forum: General Help
---

### Post by phr33k-dc on 2009-02-23
Is it possible to see the typed history in terminal?

---

### Post by estamand on 2009-02-23
try this:

cat ~/.bash_history

---

### Post by sydbat on 2009-02-23
I've been wondering this too. Is there a file that can be viewed/saved for future reference?

---

### Post by Anxious Nut on 2009-02-23
even shorter, just type "history"

---

### Post by phr33k-dc on 2009-02-23
thanks man great help

---

### Post by KeyserSoze93 on 2009-02-23
```
history > file_for_later_reference.txt
```

---

### Post by mb_webguy on 2009-02-23
That's exactly what the "history" command is for!

However, by default it only keeps track of your last (IIRC) 100 commands, and it just keeps them in a list.

To make it a bit more useful, you may want to add the following lines to the end of your ~/.bashrc file.```
shopt -s histappend
PROMPT_COMMAND="history -a;$PROMPT_COMMAND"
export HISTSIZE=5000
export HISTFILESIZE=5000
export HISTTIMEFORMAT="%d/%m/%y %H:%M  "

```
The first line ensures that commands are appended to the history, rather than overwriting it.  The second appends commands as they are executed, rather than at the end of the session, so that if you have multiple terminals open at once, the history is always up-to-date.

The third and fourth lines increase the number of commands stored in the history to 5000.  You can adjust this number as you see fit.

The last line adds a timestamp in front of each command in the history so you can see when you executed that command (and therefore sort by when you executed a command, if you want).  This will only apply to commands executed after you make this change to your .bashrc file and restart your terminal session.  All commands prior to making this change to .bashrc will have the timestamp of when you made the change.

---

### Post by phr33k-dc on 2009-02-23
how do you then delete history?

---

### Post by Slim Odds on 2009-02-23
> **phr33k-dc said:**
> how do you then delete history?

rm ~/.bash_history

---

### Post by Slim Odds on 2009-02-23
I also highly recommend this:```
export HISTCONTROL=ignoreboth:erasedups

```

---

### Post by mb_webguy on 2009-02-23
To clear the history from memory so you only see the commands issued after that for the current session, use "history -c".  To clear the history completely, use "rm ~/.bash_history".

---

### Post by mb_webguy on 2009-02-23
> **Slim Odds said:**
> I also highly recommend this:```
export HISTCONTROL=ignoreboth:erasedups

```

Hey Slim... does this work with the timestamp?

Here's another good mod to history:```
export HISTCONTROL=ignorespace:ignoredups
```
I'm not sure ignoredups works if you're using a timestamp, but what it should do is prevent repeated commands from making multiple history entries.  The ignorespace option allows you to prevent a command from being added to the history by adding a space before the command, such as " ls" instead of "ls".

---

### Post by Tek-E on 2009-02-23
if you just type
```

history

```
It will show all the commands typed at the terminal.
Of course I find it hard to read straight from the terminal so I usually send the output to a file like this
```

history > history_file.txt

```

---

### Post by mb_webguy on 2009-02-23
> **Tek-E said:**
> if you just type
```

history

```
It will show all the commands typed at the terminal.
Of course I find it hard to read straight from the terminal so I usually send the output to a file like this
```

history > history_file.txt

```

Or you could use "history | more".  Or "history | tail -n *n*" to show the last *n* lines.

---

### Post by Slim Odds on 2009-02-23
> **mb_webguy said:**
> Hey Slim... does this work with the timestamp?

Here's another good mod to history:```
export HISTCONTROL=ignorespace:ignoredups
```I'm not sure ignoredups works if you're using a timestamp, but what it should do is prevent repeated commands from making multiple history entries.  The ignorespace option allows you to prevent a command from being added to the history by adding a space before the command, such as " ls" instead of "ls".

ignoreboth is the same as ignorespace and ignoredups

don't know about the timestamps

---

### Post by tjl30 on 2011-10-12
> **mb_webguy said:**
> Or you could use "history | more".  Or "history | tail -n *n*" to show the last *n* lines.

You're forgetting the most important one history | grep without grepping my history I would be so lost...

It's seriously one of the most useful things I ever learned about Linux.

---

### Post by oldos2er on 2011-10-12
And back to sleep. Closed.

---

