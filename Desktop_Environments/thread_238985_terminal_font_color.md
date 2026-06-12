---
title: "terminal font color"
date: 2006-08-18
forum: Desktop Environments
---

### Post by hubei on 2006-08-18
i installed ubuntu6.0.6 on dell dimension 4150, it works great, functional like windows xp (some aspects it is better than xp). however there is one little glitch. in the xtermail (gnome-termainal or console etc). only one color(black) for all files(directory, gif, jpeg, etc). on other linux boxes or unix boxes, they are differentiated in some way, eg, in FC5, the directory is yellow or blue. how can i make the terminal colorful ?
thanks in advance.

---

### Post by givré on 2006-08-18
Have a look at your .bashrc file
```
gedit .bashrc
```
there should be a line about the, just uncomment it.
But i believed it was on by default.

---

### Post by hubei on 2006-08-18
thanks.

no, play around it for  a while. even i create a new account. plus i could find /etc/bashrc /etc/profile.d. reinstalled bash package, didn't work.

bubei

---

### Post by givré on 2006-08-18
Let see your .bashrc (your locale one, not /etc/bashrc)
You should have something like that :
```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi
```

---

### Post by hubei on 2006-08-18
thanks, my .bashrc doesn't have these code. after i pasted it in, it works. 
hubei

---

