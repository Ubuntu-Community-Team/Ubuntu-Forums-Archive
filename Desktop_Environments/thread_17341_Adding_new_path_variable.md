---
title: "Adding new path variable"
date: 2005-02-27
forum: Desktop Environments
---

### Post by SurreaL on 2005-02-27
Hello!

I would like to know how to automatically add a new directory into my path whenever I log into a terminal. (Whether through ssh or just by launching xterm from inside my XFce session)

I've tried to add the line - PATH=~/scripts:"${PATH}" - into my ~/.bash_profile file, however this doesn't seem to affect anything.. (Unless I manually "source" it when I log in..)

I've also tried creating a file ~/.gnomerc, and added "source .bash_profile" into that.. to see if it would force it to the file.. but that also doesn't work..

Any other suggestions?

---

### Post by cwaldbieser on 2005-02-28
Try putting something like:
```
PATH=$PATH:/home/myusername/scripts
export PATH
```
into .bashrc.  The .bashrc file is the one that gets executed every time you open up a console window.  .bash_profile only gets executed when you log on the first time.  Normally, I put most of my changes in .bashrc, and at the end of .bash_profile, I add the line:
```
source .bashrc
```

---

### Post by cka on 2005-02-28
You can make it system-wide by editting one of the /etc files...  But I don't remember offhand which one it is.  I'm fairly sure 'bash' is in the name of it however, so I'm sure you can take it from that step.   8-)

---

### Post by SurreaL on 2005-02-28
awesome! Thanks alot guys :D worked perfectly!

---

### Post by jerome bettis on 2005-02-28
editing /etc/profile and ~/.bashrc and ~/.bash_profile did absolutely nothing for me.

then one day i was stumbling around and found /etc/gdm/gdm.conf.  adding the directory to the default path line in this file did the trick.

---

