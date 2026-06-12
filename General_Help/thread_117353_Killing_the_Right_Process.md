---
title: "Killing the Right Process"
date: 2006-01-14
forum: General Help
---

### Post by mlissner on 2006-01-14
So, I've been running Ubuntu for a couple of months now, and I've got it down more or less...one thing I can't figure out: When a process needs to be killed, how do you know which one it is?

For example, when I run ps -ax, it lists a ton of processes, most of which I have no idea what they are, one of which needs to be murdered. But which? I can't go around killing aimlessly.

Any suggestions?

---

### Post by Mr_Grieves on 2006-01-14
I do like this:

1) Find out what program is giving me problems.
2) Finding out what it's binary/daemon is called. Reading abit about the program helps. Killing aimlessly is dangerous!
3) Finding out what it's process id (PID) is:
```

ps -ef | grep <name_of_program>

```
4) Either restarting the process by using:
```

kill <PID>

or killing everything with a specific name (demands abit causion):

killall <name_of_program>

```

or killing it off completly:
```

kill -9 <PID>

```

---

### Post by super on 2006-01-14
try running [FONT="Courier New"]top[/FONT] in a terminal instead.

it lists processes that use the most amount of memory/cpu (usually the ones you want to kill) along with the executable name and PID. pressing 'k' in top will give you a dialog to kill a process using the PID. you press 'q' to quit.

alternately if you want to kill an X application that has hung, run [FONT="Courier New"]xkill[/FONT]. it will change your mouse cursor into a skull & crossbones and you just click on the application window you wish to kill.

EDIT: dang! mr_grieves is fast! i i meant try this instead of what you were doing. not instead of what he suggested. :D

---

### Post by mlissner on 2006-01-14
OK. I like the skull and crossbones technique. Lovely. I'll play with it, and see how well it works.

The top thing doesn't seem to be too helpful though because the program I wanted to kill (I ended up rebooting, but this information going in my Linux Notes file), froze, and wasn't doing anything, not even using memory. 

Thanks a lot. xkill is brilliant.

Here's a follow up question though. Is there any way to determine what the name of a program will be when you go to look it up in ps so you can just match it up at that point?

---

