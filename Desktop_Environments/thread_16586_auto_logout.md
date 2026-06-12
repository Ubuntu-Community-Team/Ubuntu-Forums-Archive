---
title: "auto logout?"
date: 2005-02-22
forum: Desktop Environments
---

### Post by foobar on 2005-02-22
is there away to have unbuntu logout a user after 3 hrs of no activity?

---

### Post by GilGalad on 2005-02-22
The package autolog (from universe) does just that.

---

### Post by foobar on 2005-02-22
then, would it be-
$ sudo apt-get install autolog

?

---

### Post by GilGalad on 2005-02-23
[QUOTE=foobar]then, would it be-
$ sudo apt-get install autolog

?[/QUOTE]
 Yes. And you will need to configure it (I think in /etc/autolog.conf)

---

### Post by foobar on 2005-02-23
merci beaucoup

---

### Post by foobar on 2005-02-23
this is the default autolog.conf-
```
# Enter a regular expression for the username, group and tty line.
# All three expressions must be matched before the rest of the line will
# be applied to any process.

# If the process has been idle (or connected) more than "idle" minutes,
#    autolog will attempt to kill the process.
# If idle<0, the process is exempt.
# If idle=0, the users must not be idle for to long :) -> debugging
# If "nowarn" is asserted, the user will
#    not be warned that it is about to be killed.
# After "grace" seconds, autolog will attempt to kill the process.
# If "mail" is asserted, mail will be sent to the user
#     telling how his process met its end.
# If "hard is asserted, the process will be killed
#     after "idle" minutes of total session time (rather than idle time).
# ban=xx: A user extending his session-limit will be banned for xx minutes.

name=ppp-.*     idle=-1 line=ttyS2
line=pty.*      idle=30 grace=30 nomail nolog
group=games     idle=10 grace=60
group=lynx.*    idle=10 grace=60 clear

# protected users
name=root       idle=-1

# idle - limits
group=student   idle=15 grace=180

# session - limits
group=users     idle=60 grace=120      hard ban=20 clear
name=guest      idle=60 grace=60       hard ban=5  clear


# This makes it possible to change the options...
#      make sure, ps with its options returns one heading-line
#      and lines beginning with: USERNAME PID
#       e.g.: cj        2568
#       or  : cj        2568  0.0  0.0  1944    0 pts/2 ..... [telnet]
#      No spaces or tabs before this option, please.
# ps=ps -ef
# ps=ps aux
# ps=ps ax o user o pid

# To stop autolog from killing lost processes, umcomment the next line.
nolostkill
```

what do i need to change so that it will logout anyone who is idel for 3hrs?
there are only 2 users on this comp and no groups or anything

sry, i'm a no0b

---

