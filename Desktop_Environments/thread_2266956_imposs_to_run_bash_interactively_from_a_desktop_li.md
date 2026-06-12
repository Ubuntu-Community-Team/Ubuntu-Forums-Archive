---
title: "imposs to run bash interactively from a desktop link ? (i.e. &quot;bash&quot;, not &quot;sh&quot;)"
date: 2015-02-26
forum: Desktop Environments
---

### Post by Li_Wu on 2015-02-26
If at /home/**you**/Desktop/  one does: right click, create new, link to application, Application: command "mc", Advanced options: "run in terminal", OK

One has a new DToplink on KDE to start mc = GNU's midnight commander.

However, mc is run within  **bash**  in **sh**-mode! The difference is that ~/.bashrc is **not** executed as a startup file.
note: **/bin/sh** is a symbolic link to **bash**, not **dash**, here.

Invoking **bash** runs .bashrc;  invo&#7729;ing **sh** - however - does not run **any** startup-file, least of all .bashrc  - to sum up bash behaviour. :mad:  
see: 
[http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html#Bash-Startup-Files](http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html#Bash-Startup-Files)
[http://www.gnu.org/software/bash/manual/html_node/The-Restricted-Shell.html#The-Restricted-Shell](http://www.gnu.org/software/bash/manual/html_node/The-Restricted-Shell.html#The-Restricted-Shell)
 

This is somewhat undesirable for many **mc** users, since in the above case,  **mc** clearly does run  in factual "interactive bash mode", but KDE forces it into non-interactive mode, sadly.
The KDE desktop really seems to execute "**sh**" which invokes "**non**-interactive mode" without executing .bashrc

The drawback is that .bashrc settings such as** TERM="xterm-256color"** are ineffective now - one cannot use hicolor skins in mc now - such as in  **mc -S sand256.ini**.
The same problem appears with "file associations" asf. where the command-line invokes **sh** instead of **bash** as well, which is sometimes undesirable.
 
So, does anyone know how to have **bash** instead of **sh** executed by a desktop link or a file-association (e.g. for right-button-opening in dolphin some plain-text-files "*.txt" via mcedit in a hicolor skin) ?

What is even worse: CTRL-O subshell does not work in mc in friggin' **sh** mode  :-|  ](*,)
totally killing any reasonable workflow in mc. :twisted:

---

### Post by anujmonster on 2015-02-26
why dont you just run 'bash mc'?

---

### Post by Li_Wu on 2015-02-27
> **anujmonster said:**
> why dont you just run 'bash mc'?

/usr/bin/mc: /usr/bin/mc: cannot execute binary file

that's why  ):P 

it would only make sense it it was poss to forward the %F filename to open as in   mc -e %f    (file to edit)
I can't see how that works, even with a call of "konsole   -e  mc -e %F"

no work.  :-(

---

