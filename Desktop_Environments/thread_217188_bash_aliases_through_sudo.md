---
title: "bash aliases through sudo"
date: 2006-07-16
forum: Desktop Environments
---

### Post by mattme on 2006-07-16
Hi I've set some nice shell aliases for myself in .bashrc but these don't apply if I run these commands as sudo, so I can't make 'sudo rm' safe.

The alias function doesn't allow you to specify long aliases (alias 'sudo rm'='sudo rm -v'). Even then I'd rather not duplicate them. Putting the aliases in /root/.bashrc won't help, because the aliases are applied before execution by my user's shell, that they commence sudo is irrelevant.

any ideas? I'm sure this must be a very common problem when ppl are using sudo rather than root shells.

---

### Post by kabus on 2006-07-17
AFAIK there is no way to get sudo to recognize aliases, but there are workarounds: Either start a shell with 'sudo -s' or include sudo in the aliases that need it, eg:
```

alias agi='sudo apt-get install'
```

---

### Post by gnujoshua on 2006-08-22
Even better, 
```

alias sudo="sudo -s"

```

---

### Post by fig_wright on 2008-06-20
I'm having this issue. How can we make commands like ```
sudo rm test*.txt
``` execute automatically as ```
sudo rm -v test*.txt
``` as if rm were aliased to rm -v?

The large number of people coming from other unix environments where root is used casually will have many such root aliases. Wiping them out will just make us use sudo -s all the time, which I believe undermines the point of sudo...

I've seen some people suggest putting the aliases in /root/.bashrc - this doesnt work.

---

### Post by valadil on 2008-07-22
I haven't tried sudo -s, but the following works for me:
```
alias sudo='A=`alias` sudo  '
```
I can't remember why the A is there, but you're essentially calling all your aliases before sudo hits.  Aliases and variables listed before a command are carried into that command (ie 'DISPLAY=:0.0 xterm' will launch an xterm into the 0.0 X window, wherever you may be calling this from as long as you have suitable permissions).

---

