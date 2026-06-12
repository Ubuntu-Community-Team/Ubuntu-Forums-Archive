---
title: "How do I persistently set an enviromental variable?"
date: 2009-03-14
forum: General Help
---

### Post by Logomachist on 2009-03-14
I'd like to configure Pidgin to store its logs in the same directory as my Windows machine does. To accomplish this one sets an environmental variable PURPLEHOME to the path you want the logs saved to.

I know how to do this on Windows but in Ubuntu I am stuck. 
[LIST=1]
[*]With no constent drive letter, how do I ensure that the logs are being saved to the correct drive? The path can change every time it is mounted. Try to mount it to the same location every time? If so, can this be automated at bootup, and if so is this desireable?
[*]I know environmental variables can be set per session on the commandline, but how do I make it permanent?
[/LIST]

---

### Post by stumbleUpon on 2009-03-14
environment variables can be set permanently by editing your .bashrc file in your home folder

export environment_variable='value'

---

