---
title: "Probably an easy fix, cannot run scripts from command line"
date: 2006-01-26
forum: Desktop Environments
---

### Post by pbaehr on 2006-01-26
I'm new to linux and overcoming frustrations every day. My latest frustration is this: I download a script or an binary executable and I can't run it from the command line. I cd to it's immediate directory. I use ls to verify that it is in fact there. I use chmod to make sure it has the permissions set to be executable. I type the name of the script and it tells me it can't find it.

I can find it. It's right there. I see it plain as day. Why can't the computer? It doesn't matter if I use sudo or even log in as root.

I'm pretty sure the problem is my lack of experience and I am doing something very basic wrong. This is not an isolated problem, I've encountered it with many things I've downloaded. Sometimes I can get around it by running it via the GUI.

What am I doing horribly, horribly wrong?

---

### Post by newtonfn on 2006-01-26
did you add ./ (dot slash) before the script/bin name ??

For example.. if I am in a directory with a script called myscript.pl then y should write:
"./myscript.pl" to run it. (whitout the quotes - case sensitive - hope your filename have no spaces)

---

### Post by pbaehr on 2006-01-26
That is probably the problem. Thanks. I will try it when I get home. Out of curiosity, if I don't specify the ./ part, where is it looking for the file?

I am coming from Windows so in my experience command line entries are looked for first in the current directory and then anywhere else it thinks it might find it based on the system's PATH entry. Does this mean that Linux searches for it where it thinks it might be but won't look in the current directory unless specifically instructed?

Still learning. Thanks.

---

### Post by jrib on 2006-01-26
```
 echo $PATH 
```

That's where it looks.  Notice '.' isn't there.  As I understand it, this is basically so someone doesn't put a script called 'ls' in a directory (let's say your $HOME for example).  When you type 'ls' in your home directory the script would run instead of what you want.  A bad person could make that script do very bad things...

---

### Post by newtonfn on 2006-01-26
I have a strong Windows background too. I am still a linux newbie. (that speaks Spanish.. that's why my terrible English :oops:)

Linux do use the system PATH just like Windows.
But it won't look in the current directory unless the current directory is in the system path.

By default the current directory is not in the system path.. so Linux won't look for executables in it.

If you want the current directory always looked for, add it to the path modifying the file .bashrc in your home directory and adding a line like:
export PATH=$PATH:.

I don't know why the current directory is not there by default.. I think have something to do with security but in no time you get acquired to write always ./ :)

---

### Post by pbaehr on 2006-01-26
That makes a lot of sense now. Very helpful responses. Thanks for explaining it!

---

