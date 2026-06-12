---
title: "commands problem"
date: 2012-08-01
forum: Desktop Environments
---

### Post by Priyank Kaushal on 2012-08-01
hi,

I was trying to add a path in bash file.....but i don't how i deleted some thing..its showing this message..please help..
:~$ vi .bashrc
Command 'vi' is available in '/usr/bin/vi'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
vi: command not found

So please help....what to do??

---

### Post by levlaz on 2012-08-01
What exactly are you trying to do?

---

### Post by Priyank Kaushal on 2012-08-01
actually i was trying to add path in terminal...

---

### Post by drmrgd on 2012-08-01
First depending on how you modified the $PATH variable, it should only be effective in the current shell you're in.  So, if you exit your terminal window and start a new one (or just start a new shell environment), your $PATH variable should be back to normal.  It will only be permanently changed if you change you .profile.


If that doesn't fix it, it might be helpful to find out what's going on with your current $PATH variable.  Please post the output of:

```
echo $PATH
```

---

### Post by cortman on 2012-08-01
drmrgd gives good advice; just an FYI a quick and dirty solution is to add it to your path:

```
PATH=$PATH:/usr/bin
```

Although I must say that missing something as fundamental as /usr/bin probably should be fixed the right way.

---

### Post by Priyank Kaushal on 2012-08-02
yes i tried it...it got fixed...
thank u

---

