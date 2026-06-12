---
title: "bash in vi editing mode"
date: 2009-01-03
forum: General Help
---

### Post by sani07 on 2009-01-03
[FONT="Courier New"]Hello Guys

In Xubuntu 8.10 I run Terminal 0.2.8. While the bash shell is in vi editing mode, even the basic vi commands do not work.

Here is an example:

With the following command I switch to vi editing mode:
sani@ws001-lnx:~$ set -o vi

Just for example I write a fony command:
sani@ws001-lnx:~$ this is command

I hit <Esc>2b and expect the cursor jump to "i" as follows:
sani@ws001-lnx:~$ this **[SIZE="3"]i[/SIZE]**s command


but instead the cursor jumps up into the prompt string to the character "a" as follows:
s**[SIZE="3"]a[/SIZE]**ni@ws001-lnx:~$ this is command



In vi editor the command <Esc>2b works as expected, why in bash there is a problem? What is wrong?

How can I use bash in vi editing mode?

Thanks for answer[/FONT]

---

### Post by dagnabit dang doohickey on 2009-01-03
FWIW: I just tried your example on my dapper install and it works as expected.

---

### Post by sani07 on 2009-01-03
what is dapper install?

---

### Post by dagnabit dang doohickey on 2009-01-03
Ubuntu 6.06 Dapper Drake

---

### Post by sdennie on 2009-01-03
Your "set -o vi" command is correct.  What graphics drivers are you using?  nvidia?  Is it possible that it's screen corruption?  For example does this work:

```

$ ls /usr<Esc>bcwlib

```

---

### Post by sani07 on 2009-01-03
Yes vor, your example works OK.

I am very new in Linux, how can I say what video driver I am using?

---

