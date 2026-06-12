---
title: "How can I increase the bash history size"
date: 2009-05-11
forum: General Help
---

### Post by lavinog on 2009-05-11
I was going over one of my servers and found something weird...I figured out where it came from, but it would have been nice if I could go further back in the bash history file

Anyone have any ideas on how I can do this?
I am thinking one way would be to use a cronjob to make a backup of the ~/.bash_history file

---

### Post by philinux on 2009-05-11
Do you mean scrolling back in the terminal or the size of .bash_history.

---

### Post by lavinog on 2009-05-11
size of .bash_history

---

### Post by kanikilu on 2009-05-11
You can set a new size in ~/.bashrc to increase the lines in .bash_history. I think the default is 500 lines, so if you wanted to double it, just add **HISTSIZE=1000** in your .bashrc file.

Another possible solution would be to use logrotate - I understand the concept, but it's a bit over my head, so I'll just point you to the page I was looking at...

[http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-12/msg00864.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-12/msg00864.html)

---

### Post by lavinog on 2009-05-11
thanks, I will try the .bashrc option

---

### Post by philinux on 2009-05-11
echo $HISTFILESIZE to check

and
echo $HISTSIZE as above to increase. When you do it it also shows the old and new size.

Also see

man bash

scroll right down to the HIST stuff.

---

