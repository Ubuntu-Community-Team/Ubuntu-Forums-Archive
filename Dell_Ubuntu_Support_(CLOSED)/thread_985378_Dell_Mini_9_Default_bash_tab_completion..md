---
title: "Dell Mini 9 Default bash tab completion."
date: 2008-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kevinality on 2008-11-17
OOB, bash tab completes the first keyword but does not tab complete anything beyond that first level, e.g,

if I want to type sudo aptitude update, I can type sud <tab>, but I can't then type apti <tab>, and the same with upd <tab>.

Does anyone else have this issue and/or knows how I can change its behavior?

---

### Post by dimebar on 2008-11-17
> **kevinality said:**
> OOB, bash tab completes the first keyword but does not tab complete anything beyond that first level, e.g,

if I want to type sudo aptitude update, I can type sud <tab>, but I can't then type apti <tab>, and the same with upd <tab>.

Does anyone else have this issue and/or knows how I can change its behavior?

You need to uncomment the following section of your .bashrc file as below:

```

# enable programmable completion features (you don't need to enable 
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile 
# sources /etc/bash.bashrc). 
if [ -f /etc/bash_completion ]; then 
    . /etc/bash_completion 
fi 

```

---

