---
title: "Sorting the selection in Kate"
date: 2010-01-29
forum: Desktop Environments
---

### Post by dargaud on 2010-01-29
Hello all,
Kate has lately became my editor of choice while in a GUI. But I find it lacks many not so advanced features. In particular I would like the possibility to sort a block of selected text, line by line. I see a [Configure][Extensions][Scripts] menu, but it's all blanks. Am I missing something ?

Is there a simple way to pipe the selection through a command line and replace the block with the result ?

---

### Post by MazeChaZer on 2013-01-28
I know this thread is old, but because it's one of the first results in Google let me quote form the KWrite-Devel mailing list[1]:

> Install the text filter plugin, select lines, activate the plugin (tools->text 
filter) and enter the command 'sort' (given sort (1) is installed on your 
(uinx) system)This worked for me ;)

[1] [http://lists.kde.org/?l=kwrite-devel&m=118270596423948](http://lists.kde.org/?l=kwrite-devel&m=118270596423948)

---

### Post by dargaud on 2013-02-12
Thanks. I had figured it out earlier and should have posted a reply here. I just with the last command would remain in the box and also that you were able to recall the last command with a simple shortcut key.

---

### Post by PJSingh5000 on 2013-07-15
Does anyone know of a plugin with a GUI dialog to select sort options (like the gedit sort plugin)?

---

### Post by dargaud on 2013-07-18
You might as well learn the 2~3 options to sort that you use regularly and use those with Ctrl-\, it'll be faster than any GUI. 'man sort' and then mostly '-u', -f', '-n', '-r'

---

