---
title: "View User's Shell"
date: 2009-06-12
forum: General Help
---

### Post by nexxus92 on 2009-06-12
Hey I am new to ubuntu and am wondering how to set something up. It is rather complicated to explain so im sorry if not everyone understands what I am trying to accomplish. So, a couple of years ago a friend of mine created an account for me on his BSD computer so i could ssh to it and explore a little. Everytime i would ssh into my account and get onto my shell, my friend could see everything i typed and type as me in my shell. I am trying to figure out how to do the same thing just on an ubuntu machine. The closest i have gotton is inputting this command: cat /dev/pts/5 | tee -a pts0log but that did not work as well as i had hoped it to.

---

### Post by whoop on 2009-06-12
maybe he was viewing the .bash_history of the account you where using.

---

### Post by nexxus92 on 2009-06-12
I thought of that but he could type directly onto the current shell i was on so he was somehow on my shell. He said he used the watch command or something.

---

### Post by niteshifter on 2009-06-12
> **nexxus92 said:**
> I thought of that but he could type directly onto the current shell i was on so he was somehow on my shell. He said he used the watch command or something.

He did indeed use the watch command, on BSD systems this is a tty snooper program. The Linux watch command is an altogether different critter - it watches the output of a command. The equivalent to BSD's watch in Linux is ttysnoop.

---

### Post by nexxus92 on 2009-06-12
Ok awesome that make a lot more sense now! I installed ttysnooper and ran it but it says it cant connect to server when i input ttysnoop tty7 or something. Anyone know how to fix this so it can connect to the server?

---

### Post by niteshifter on 2009-06-12
Hi,

FYI, ttysnoop configuration is tricky, you can utterly hose connectivity to the box. Practice on a VM or a spare box if you can.

Read the man page first. Next read [this page]("http://www.linuxhelp.net/guides/ttysnoop/").

---

### Post by nexxus92 on 2009-06-12
Ok thanks mate

---

### Post by albinootje on 2009-06-12
> **nexxus92 said:**
> I installed ttysnooper and ran it but it says it cant connect to server when i input ttysnoop tty7 or something. 

If you would want to work as a team on things together in a console, you can also use "screen" for that.

I forgot the exact setup for that (A friend made me use it some years ago), but it might be a combination of "screen -x" and some other screen command.
If you're bored, try : man screen ;-)

---

