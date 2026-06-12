---
title: "Deleting rebellious environment variable"
date: 2011-02-19
forum: Desktop Environments
---

### Post by UltraZone on 2011-02-19
Hello all, I'm having a bit of a problem with a pesky old environment variable that I created maybe a year ago or so, now I would like to change it and for the life of me, this thing is like a zombie! It just won't die! huh? Ok, so, I did my due diligent research, I checked all these common files where environment variables are strewn around, to see if I did indeed set it in there and forgot about it: /etc/bash.bashrc, /etc/environment, ~/.profile, ~/.bashrc . Nothing.  So just to be clear, I got this environment variable that I set a long time ago, now when I open a terminal and type "zombie_variable=newstuff; export zombie_variable", it sets it only for that session of terminal.  If I start another terminal and do "env" the oldstuff comes up.  I just can't seem to be able to either kill the variable or change its content permanently... where should I look?

---

### Post by slakkie on 2011-02-19
what is the name of the zombie variable?

You can also use the unset command.

unset ZOMBIE and it should be gone.. and/or use export ZOMBIE="" but, I guess finding where it is would be more usefull ;)

---

### Post by AlphaLexman on 2011-02-19
This should do the trick, just change **maxdepth** to your liking.```
find . -maxdepth 1 -type f | xargs grep "ZOMBIE_VAR="
```You may want to check in your $HOME directory and /etc/.

---

### Post by slakkie on 2011-02-19
> **AlphaLexman said:**
> This should do the trick, just change **maxdepth** to your liking.```
find . -maxdepth 1 -type f | xargs grep "ZOMBIE_VAR="
```You may want to check in your $HOME directory and /etc/.

grep -r ZOMBIE $HOME /etc will do the trick as well. maxdepth 1 is the same as grep ZOMBIE $HOME/* /etc/*

And there is no need for xargs:

```

find /etc $HOME -type f -exec grep ZOMBIE {} + 
# or this one (is a bit slower)
find /etc $HOME -type f -exec grep ZOMBIE {} \; 

```

---

### Post by UltraZone on 2011-02-25
Slakkie: thanks, that first line of code did it.  It turns out that the environment variable was buried deep in a shell script located in /etc/profile.d that was created automatically when I installed the program and configured it.

So, moral of the story is: environment variables could be located in ANY bash (or other shell) script file, created by a user or process.

---

