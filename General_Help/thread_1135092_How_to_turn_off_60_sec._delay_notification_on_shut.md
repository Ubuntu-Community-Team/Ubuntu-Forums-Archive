---
title: "How to turn off 60 sec. delay notification on shutdown?"
date: 2009-04-24
forum: General Help
---

### Post by Chainz on 2009-04-24
Anybody has any idea on how to turn off 60 sec. delay notification on shutdown?

It's bit annoying when I try to turn off, logout or restart my machine, and it asks me if I'm sure what I'm doing and gives me 60 seconds timer to make up my mind! - Of course I'm sure!

More over, after hitting shutdown button, on that confirmation window, it gives me 3 loud beeps from the motherboard!
I usually work at night and that beep wakes up my wife (and that makes her willing to kill me #-o)!

And please, I don't want to turn manually off my internal speaker.


Anybody HELP please... [-o<

---

### Post by Peter09 on 2009-04-24
Hitting the enter will go straight to shutdown - as for the beeps ....?

---

### Post by Darkshade on 2009-04-24
About the delay:
right click your user switcher applet on the panel -> preferences -> uncheck "show confirmation window..."

About the beep (the most annoying thing in the world imo):
Add ```
blacklist pcspkr
```
in a new line to your /etc/modprobe.d/blacklist.conf file, then reboot your PC.

---

### Post by Chainz on 2009-04-24
Thanks for the replay.

But blacklisting speaker will totally turn it off, the question is on how to disable it just for that event?

---

### Post by jweber on 2009-04-27
I think this [_thread_]("http://ubuntuforums.org/showthread.php?t=1139490&highlight=beep") has a solution to your problem with the beeping during shutdown.

---

### Post by Chainz on 2009-04-28
Thanks! That should solve it!
Will test it soon.

---

### Post by Chainz on 2009-06-22
```
$ blacklist pcspkr
bash: blacklist: command not found
```

Power management preferences either didn't worked out :(

---

### Post by Cheesemill on 2009-06-22
You need to read Darkshade's post again, blacklist isn't a command.

---

### Post by Chainz on 2009-06-23
> **Cheesemill said:**
> You need to read Darkshade's post again, blacklist isn't a command.

Ohhh... me blind... :cool:
Thank you so much!

---

