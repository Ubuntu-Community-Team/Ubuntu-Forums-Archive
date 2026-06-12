---
title: "Xfce terminal colors"
date: 2012-02-28
forum: Desktop Environments
---

### Post by rattskjelke on 2012-02-28
On all (or most) of the other linux distros that I have tried, running the **ls** command in a terminal window lists the different file types in different colors.
On Xubuntu 11.10 this doesn't happen, even though the Xfce terminal has a color pallette setting. Everything is the same color except the cursor.
Is it supposed to be like this or did I break something?

---

### Post by sudodus on 2012-02-28
I have colours for the ls output in my xubuntu 11.10. I am not sure if I have changed it from the default value. Anyway the setting is in .bashrc
```
gedit ~/.bashrc
```
Look for a line like this
```
alias ls='ls --color=auto'
```
There should be another similar line for grep.

But if you log in via a 'dumb' terminal, the colours are not activated.

---

### Post by rattskjelke on 2012-02-28
I don't have a .bashrc for some reason.

---

### Post by rattskjelke on 2012-02-28
I copied the .bashrc file from the live CD. That fixed it.

---

