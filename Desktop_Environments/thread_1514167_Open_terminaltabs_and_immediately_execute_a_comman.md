---
title: "Open terminal/tabs and immediately execute a command"
date: 2010-06-20
forum: Desktop Environments
---

### Post by Tronman on 2010-06-20
Hi there,

Hoping someone can give me some advice:

I'm trying to write a simple script I can use with a launcher that will do the following:

1) Open a single Gnome terminal window
2) Open two additional tabs 
3) Execute a separate command on each of the three tabs

I've been trying to figure out how to do it with the gnome-terminal and various options of the -e and -x options, but I'm not having much luck. If nothing else, the ability to launch a terminal and then immediately execute a command would be helpful (but not for all launches of the terminal, other I'd put it in .profile or .bashrc or something)

Thanks!

---

### Post by sanderd17 on 2010-06-20
a dirty trick but you can use xdotools to simulate keystrokes like alt+T to get extra tabs or to just type a command.

---

### Post by weirdtalk on 2010-06-20
I don't know how to do that on gnome-terminal but for konsole you could do this:

```

konsole -e "command 1"
konsole --new-tab -e "command 2"
konsole --new-tab -e "command 3"

```

but note that any command that runs and quits fast (like 'ls') will run and close the tab too fast to see. If you run a command that stays open ('top', 'vim', 'nano', etc.) it will stay up.

To deal with this you can dump the comands into a script like this:
```

#!/bin/bash
command 1
read

```

and run the command with 'konsole -e "bash command1.sh"'

I'm sure gnome terminal has something similar.

p.s. I'm curious, what is it your trying to do with 3 terminals?

---

### Post by Tronman on 2010-06-20
Hey guys, thanks for your help!

Looks like I can do it with the -e option. Instead of --new-tab (in Konsole), I use --tab instead, so like this:

gnome-terminal --tab -e "bla" --tab -e "bla2" --tab -3 "bla3"

That'll open up a new window with three tabs, which should be close enough since I'll be using a launcher anyway.

The answer to your question is probably why I couldn't get it to work in the first place. I have to be on three ssh terminals at once, and was looking for a short cut to simply launch them quickly instead of manually launching them all each time and typing nearly the same command three times in a row. Lazy, I know, but cool automation like that is one of the reasons I love Linux so much in the first place! 

Anyway, when I was first trying it, the window would launch and simply hang so it didn't seem to be working. Turns out the ssh server was just being laggy! Oh well, still learned something new :)

Thanks!

---

