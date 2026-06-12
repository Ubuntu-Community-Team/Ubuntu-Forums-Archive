---
title: "unix DISPLAY environment in jaunty 9.0.4"
date: 2009-05-07
forum: Desktop Environments
---

### Post by yasheshb on 2009-05-07
hi. 

  i've installed jaunty amd64 server and created a single user "user1". 

i then logged in the gui mode (gnome desktop) and started a terminal

Applications -> Accesories -> Terminal

this brings up a terminal window (gnome-terminal)

i then checked the DISPLAY variable

```
yvb@bfc33:~$ env | grep DISPLAY
DISPLAY=0.0
yvb@bfc33:~$ 
```and started emacs

$ emacs

this brings it up in the terminal itself giving the error message
Display 0.0 unavailable, simulating -nw


when i change the DISPLAY to
```
yvb@bfc33:~$ export DISPLAY=:0.0
```and type emacs it comes up fine.

so what should be the correct DISPLAY environment variable for a default ubuntu user ?
what's the difference between

```
DISPLAY=0.0
and 
DISPLAY=:0.0

```thanks in advance.

yashesh

---

### Post by yasheshb on 2009-05-07
found out more at  - [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

but it seems that my ubuntu install is not smart enough to figure out the DISPLAY variable

> Manually setting the "DISPLAY" environment variable's value is rarely needed now days since it can be automatically and intelligently be adjusted by many applications such as "GDM" and "SSH" when needed.

anybody seen this problem before ?

thx.

yashesh

---

