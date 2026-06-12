---
title: "The program is currently not installed"
date: 2009-01-09
forum: General Help
---

### Post by adit on 2009-01-09
If I type random characters into the bash shell, it immediately says "command not found"
If I type any package names like 'anjuta' I get this output
"The program 'anjuta' is currently not installed"
How does bash recognises that it is only a package name not an unavailable command, even if 'anjuta' is not in the executable search path

---

### Post by halovivek on 2009-01-09
> **adit said:**
> If I type random characters into the bash shell, it immediately says "command not found"
If I type any package names like 'anjuta' I get this output
"The program 'anjuta' is currently not installed"
How does bash recognises that it is only a package name not an unavailable command, even if 'anjuta' is not in the executable search path

if you want read more [here]("http://www.cyberciti.biz/tips/an-example-how-shell-understand-which-program-to-run-part-ii.html"). you will find some answers

---

### Post by adit on 2009-01-23
I have understood a little bit.  The executable search path is not the first thing bash looks into.  Before that bash looks into several things.  I want to know some more.

Where exactly the word 'anjuta' is? (In which file?)
Which file bash looks into before giving me the output "The program 'anjuta' is currently not installed."

---

### Post by mssever on 2009-01-23
> **adit said:**
> I have understood a little bit.  The executable search path is not the first thing bash looks into.  Before that bash looks into several things.  I want to know some more.

Where exactly the word 'anjuta' is? (In which file?)
Which file bash looks into before giving me the output "The program 'anjuta' is currently not installed."
At least in Ubuntu, when Bash can't find a command, it runs command-not-found, which is a Python script. command-not-found searches the package database for a package containing a command by the name it's given (e.g., anjuta). If it finds such a name, it prints a message telling you how to install the program. Otherwise, it prints a generic error.

---

### Post by cariboo on 2009-01-23
When you type a term that is in the command-not-found database it will come back with a suggestion that the package be installed.

Jim

---

