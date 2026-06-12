---
title: "Remotely and cleanly shut down a process/program"
date: 2009-05-04
forum: General Help
---

### Post by jame86 on 2009-05-04
Hey,

I have been looking around for away to remotely and cleanly shutdown a program/process.

Basicly I want to remotely shutdown my bittorrent program (azureus), so as to stop the downloads and free up the network.

I already have ssh access, an tunneled vnc.  But I am after something that I can turn into a batch file for someone (less knowlegable) to run when they need to free up some bandwidth.  So I thought I might come to the brains that are the Ubuntu Forums.

So is there a console command to terminate a program cleanly.  The cleanly being the main word, as Azerus has a habbit of loosing torrents if its killed.

Thanks all,

Damingo

---

### Post by Alterax on 2009-05-04
You'll love this. The command is called "kill"

Let's say I am running iceweasel but I need to kill it remotely.  I'll need to get the process ID for it, so I ssh in and use this command:

ps ax | grep iceweasel
(which lists the process IDs and shows me which ones contain iceweasel)
Let's say it comes back with iceweasel running as PID 3945
(NOTE:  THIS NUMBER CHANGES EVERY TIME YOU LAUNCH IT)

then I would kill it with the command kill -15 3945.
the number -15 means to kill it nicely, to act as if it were closed out by a user.

Using -9 instead of -15 means to drop it immediately.  Only use this if it WON'T give up the ghost.

Another option is to use killall.

Let's say you wanted to kill off all copies of iceweasel that you are running.  SSH in and issue this command:

killall iceweasel

Got it?

---

### Post by jame86 on 2009-05-04
That does solve the "killing" issue.  Anyway to ensure the close is clean.  e.g. a Quit??

thanks 

d

---

### Post by lovinglinux on 2009-05-04
I don't have a solution for Azureus, but I would like to suggest using Deluge instead. It is specially nice for remote connection, since you can connect to Deluge's daemon via ssh, remote gtk or webui.

With the remote gtk it feels like a regular client, but it is actually connected to your remote machine. It's really nice. You can do whatever you need to do remotely, including pausing torrents and stopping the daemon on the remote machine.

More info at [http://dev.deluge-torrent.org/wiki/Faq](http://dev.deluge-torrent.org/wiki/Faq)

---

### Post by jame86 on 2009-05-04
Thanks for that I will take a look.

D

---

