---
title: "alias for all users"
date: 2009-03-12
forum: General Help
---

### Post by oliv66 on 2009-03-12
Hi all, 

I am under Ubuntu 8.10. I just installed a new PC with 3 users (accounts).

I know how to create a customized prompt (PS1) + aliases in bashrc in home.

What I would like is :

create only once aliases for every different user without modifying each .bashrc in their home.

I tried to modify /etc/profile with no success.

Is there a way to do it or should I really modify each .bashrc ?

Thanks for help,

Olivier

---

### Post by taurus on 2009-03-12
When you modify /etc/profile or /etc/bash.bashrc, you need to log out and back in again.

---

### Post by oliv66 on 2009-03-12
Hi Taurus,

Thanks for your reply but it doesn't work.

I see that I could use next time /etc/skel/.bashrc to create aliases for everybody.

But by adding the following code into /etc/profile, it doesn't work. I logged out as suggested.

```
PS1="\[\033[01;34m\][\[\033[01;31m\]\u\[\033[01;34m\] \W] $ \[\033[00m\]"


## ajouts Olivier 
alias rezo="sudo watch netstat -alpe --ip" 
alias lsnew="ls -al --time-style=+%D | grep `date +%D` " 
alias iso2cd="cdrecord -s dev=`cdrecord --devices 2>&1 | grep "\(rw\|dev=\)" | awk {'print $2'} | cut -f'2' -d'=' | head -n1` gracetime=1 driveropts=burnfree -dao -overburn -v"

# Make a long history list and history file. 
export HISTSIZE=10000000 HISTFILESIZE=10000000


## ls colorisé
alias ls='ls --color=auto'

## conversion des permissions en octal
alias lsoctal="ls -l | sed -e 's/--x/1/g' -e 's/-w-/2/g' -e 's/-wx/3/g' -e 's/r--/4/g' \
 -e 's/r-x/5/g' -e 's/rw-/6/g' -e 's/rwx/7/g' -e 's/---/0/g'"

shopt -s histappend
shopt -s cdspell
export HISTCONTROL=ignoreboth
```

any other idea ?

Olivier

---

### Post by oliv66 on 2009-03-13
Many thanks Taurus.

yesterday night, I just test with /etc/profile and it didn't work.

The solution was with /etc/bash.bashrc

have a good day,

Olivier

---

### Post by oliv66 on 2009-03-13
Many thanks Taurus.

Would you have any idea why the customized prompt is not available for every user ?

Olivier

---

