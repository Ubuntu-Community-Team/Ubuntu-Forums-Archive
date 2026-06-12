---
title: "Not quite up on lingo...  need help"
date: 2009-03-16
forum: General Help
---

### Post by WolfyAU82 on 2009-03-16
Okay I know Windows has the retarded "Blue-Screen-'O-Death", but recently came across what Linux has in a LXF cartoon.

Correct me if I am wrong, but isn't the "Kill Command" ALT+Control+Backspace?

The other two things I have no knowledge on are Daemon and Zombie Processes, What are they exactly?

---

### Post by taurus on 2009-03-16
<Ctrl><Alt>Backspace just restarts the X server.  The kill command is **kill -9 PID** or **killall app**.  And of course, you need root privilege to kill a process unless you start that app.

---

### Post by WolfyAU82 on 2009-03-17
pretty much found out what a Zombie is...  The programs that show up on the Processes as "Sleeping" and are non-responsive.  Am I right?

Anyway what are Daemons???

---

### Post by fieroboom on 2009-03-17
> **WolfyAU82 said:**
> pretty much found out what a Zombie is...  The programs that show up on the Processes as "Sleeping" and are non-responsive.  Am I right?

Anyway what are Daemons???

Daemons will take your soul!!! :D

A [daemon](http://en.wikipedia.org/wiki/Daemon_(computer_software)) is a background listening process that waits for a certain event or time to do something.
[http://en.wikipedia.org/wiki/Daemon_(computer_software](http://en.wikipedia.org/wiki/Daemon_(computer_software))
-Paul

---

### Post by arapa on 2009-03-17
daemons are the linux equivalent of Windows services or old Mac OS 9 extensions.

---

### Post by meindian523 on 2009-03-17
> **WolfyAU82 said:**
> pretty much found out what a Zombie is...  The programs that show up on the Processes as "Sleeping" and are non-responsive.  Am I right?

Anyway what are Daemons???
And no,zombies are not the one's which are sleeping,the ones which are sleeping are responsive but they are waiting for something to occur before they continue executing,and go back to sleep again,after they process whatever they were waiting for.
Zombies:
[http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)

In short: (and highly simplified,maybe over simplified)
If you start Movie Player,it starts as a child process of the Xorg(also known as X server,mentioned above),which is the GUI you see when you have just finished booting the PC.
Now if Movie player stops executing,but Xorg is busy with something else,it cannot read that Movie Player has completed execution,thus Movie Player becomes a zombie process,that is it's dead,but if you look at all the processes waiting for execution,it will show up,thus dead,but not completely,equivalent to zombie.

---

