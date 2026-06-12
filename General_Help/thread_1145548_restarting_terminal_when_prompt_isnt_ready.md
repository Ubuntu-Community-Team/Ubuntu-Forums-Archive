---
title: "restarting terminal when prompt isnt ready"
date: 2009-05-01
forum: General Help
---

### Post by Jimmynemo2 on 2009-05-01
Howdy, 

When I am in a terminal, sometimes after a command, it doesnt "reset" the terminal to be ready for a new command.

I've been closing that window and opening a new one each time, but I cant help but feel I'm missing something.

Only problem, I look online, and can find a billion ways to reboot the computer from the terminal, but not to reboot the terminal itself.

I've included a screenshot to show what I mean by "not ready."

Thanks in advance.

---

### Post by taurus on 2009-05-01
<Ctrl>c

---

### Post by Jimmynemo2 on 2009-05-01
Wow, thanks. That totally explains my previous confusion of why the terminal changed Control+C to Control/Shift C to copy - since apparently that was in use.

Thanks for the help, I sure appreciate it.

---

### Post by lensman3 on 2009-05-01
The other "thing" that happens  is when you dump a binary file to the screen and the prompt goes to very strange characters.  The way to recover from that problem is to type in "CNTL-M reset CNTL-M" (don't put in the spaces around reset or the quotes).  The terminal will pause for a couple of seconds, clear out the junk, and the correct prompt will show up.

---

