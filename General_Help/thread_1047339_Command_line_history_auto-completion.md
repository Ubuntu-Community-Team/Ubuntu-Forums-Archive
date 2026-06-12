---
title: "Command line history auto-completion"
date: 2009-01-22
forum: General Help
---

### Post by sambarluc on 2009-01-22
I found this interesting feature of command line history, to scroll through entries only beginning with a few typed characters, to be added to ~/.inputrc:

# non-incremental search of history based on the text between the prompt and the cursor
# up arrow
"\e[B": history-search-forward
# down arrow
"\e[A": history-search-backward

But I get this error:

bash: \e[B:: command not found
bash: \e[A:: command not found

Does anyone knows what I am missing? I am not an expert...
Thanks!

---

### Post by malfist on 2009-01-22
You can do Ctrl+R to search for a string in your history.

---

### Post by sambarluc on 2009-01-22
Yes, I know, but I am looking for this different feature. It is often a much faster solution to start typing the command and then just scroll with the arrows.

---

### Post by Slim Odds on 2009-01-22
> **sambarluc said:**
> I found this interesting feature of command line history, to scroll through entries only beginning with a few typed characters, to be added to ~/.inputrc:

# non-incremental search of history based on the text between the prompt and the cursor
# up arrow
"\e[B": history-search-forward
# down arrow
"\e[A": history-search-backward

But I get this error:

bash: \e[B:: command not found
bash: \e[A:: command not found

Does anyone knows what I am missing? I am not an expert...
Thanks!

When do you get this error?

Some details would be very helpful and might actually get you an answer.

---

### Post by sambarluc on 2009-01-22
> **Slim Odds said:**
> When do you get this error?

Some details would be very helpful and might actually get you an answer.

Sorry...

The error appears with:
```
. .inputrc
```

---

### Post by Slim Odds on 2009-01-22
> **sambarluc said:**
> Sorry...

The error appears with:
```
. .inputrc
```

.input is not a bash script, so you can't source it (.)

it is loaded by readline

Just start a new shell (i.e., terminal window) to use the changes....

---

### Post by dagnabit dang doohickey on 2009-01-22
You don't reload inputrc by sourcing it. Reread inputrc with the following key sequence: **Ctrl-x**, **Ctrl-r**

---

### Post by sambarluc on 2009-01-22
> You don't reload inputrc by sourcing it. Reread inputrc with the following key sequence: **Ctrl-x**, **Ctrl-r**

Mmm... interesting, now not even standard history is working :D

---

