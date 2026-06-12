---
title: "Trouble with a terminal launcher"
date: 2009-06-08
forum: Desktop Environments
---

### Post by shutt3r on 2009-06-08
I am trying to create a launcher in my gnome panel that will launch a terminal in a particular directory and execute a command, in this case "md5sum --help".  

My problem is that any command I try to execute as a launcher will open a terminal and immediately close the terminal once the program exits.  I want the terminal to stay open once the command completes.

Here's what I've tried so far:

gnome-terminal -x md5sum --help (runs and exits window)

I've changed the default profile to keep window open after command execution (hangs terminal window)

tried putting command in a bash script and called the script from the launcher (exits terminal as well)

If anyone can help I would greatly appreciate it.

---

### Post by MyR on 2009-06-08
gnome-terminal -e 'md5sum --help'
is actually what runs the command you want but i'm not sure how to keep the terminal open :|

peace

---

### Post by shutt3r on 2009-06-09
I tried the -e option as well.  You would think this would be a simple task.. :-k  Thanks for trying!

---

### Post by shutt3r on 2009-06-09
bump

---

### Post by synapsys on 2009-06-09
Have you tried putting a & at the end?

```
gnome-terminal -e md5sum --help &
```

---

