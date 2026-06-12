---
title: "editting the history program"
date: 2009-01-25
forum: General Help
---

### Post by lastfrontier on 2009-01-25
is it possible to edit the history program i want to increase it to the last 1500 commands entered i cant seem to find the .config file for that particular program

---

### Post by dcstar on 2009-01-25
> **lastfrontier said:**
> is it possible to edit the history program i want to increase it to the last 1500 commands entered i cant seem to find the .config file for that particular program

[http://www.catonmat.net/download/bash-history-cheat-sheet.pdf](http://www.catonmat.net/download/bash-history-cheat-sheet.pdf)

---

### Post by lastfrontier on 2009-02-06
thanks

---

### Post by mb_webguy on 2009-02-07
Here's what I appended to the end of my ~/.bashrc file to improve my history:```
shopt -s histappend
PROMPT_COMMAND="history -a; $PROMPT_COMMAND"
export HISTFILESIZE=5000
export HISTSIZE=5000
export HISTTIMEFORMAT="%d/%m/%y %H:%M "

```

The first makes sure the current session history is appended to the history file.  I don't quite remember why I added the second, to be honest.  The third and fourth tell it how many commands to remember and how many to display when you call it up, respectively, and the last prefaces the commands with a nice timestamp, so I can search and sort my history by when I used the command.

---

### Post by lastfrontier on 2009-03-07
well this seemed to work so thank you very much i had a friend who changed the history program to 0 but he could not remember how he did it

---

### Post by lastfrontier on 2009-03-07
ok i guess this did not work if i reboot i still only get my last 500 commands but it dose store more then 500 as long as i dont reboot i want the last 1000 or 2000 commands to be stored i was wondering if there is a .confg file to edit out there?????

---

