---
title: "how set path of run application dialog?"
date: 2005-07-15
forum: Desktop Environments
---

### Post by chumpytown on 2005-07-15
Hello,
I just started using Ubuntu after having used Fedora for a while.  I liked how in Fedora, it was possible to add executables to ~/bin and then be able to run them from the "run application..." dialog (Applications->Run Application).  However, this doesn't seem to work in Ubuntu, unless I put them in /usr/local/bin.  I want the Run Application's search path to be per user, so placing execs in /usr/local/bin is not desirable.

Key question: How can I modify the search PATH of Run Application on a per user basis?  

Thanks for any support!  :smile: 

-david

---

### Post by wylfing on 2005-07-15
The "right" place to modify PATH is kind of a mystery these days. My current recommendation, if you are accustomed to booting into Gnome, is to add an export command to the session's startup programs. From the main menu, choose System > Preferences > Session, click the Startup Programs tab, click Add, and enter something like this:
```
export PATH=$PATH:~/bin
```

---

### Post by chumpytown on 2005-07-26
Hmm unfortunately this doesn't seem to effect any change.  I tried restarting x, with no change.  Any other place I can let path include ~/bin?

---

### Post by professor_chaos on 2005-07-26
Well.... export PATH=$PATH:~/bin
should add this dir to your path for that shell session.
To verify, type "export" and you should see it listed under declare -x PATH

You can add this path forever, by adding this to your ~/.bashrc file.

Of cource all of this is for bash.

---

### Post by jsaumer on 2005-07-26
I have been having the same problem trying to get the java path onto my PATH variable... 

I have tried adding it to my /etc/profile and that didn't work
I've tried adding it to /etc/enviroment and that didn't work either

I am 100% confused on where to modify this path variable in ubuntu  :neutral:

---

