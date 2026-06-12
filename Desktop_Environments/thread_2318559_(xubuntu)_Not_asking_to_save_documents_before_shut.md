---
title: "(xubuntu) Not asking to save documents before shutdown/restart"
date: 2016-03-27
forum: Desktop Environments
---

### Post by gorbeich on 2016-03-27
Hi,

I'm using Xubuntu 14.04.4 LTS. When shuttingdown/restarting is not asking to save unsaved documents. Is there a way to force asking before shuttingdown/restarting? Sometimes I've forgotten to do so and have lost information.

Regards.

---

### Post by TheFu on 2016-03-27
I don't know of any solution to this issue.  You'd need to list each of the programs and contact those individual project teams.

BTW, many programs have an "autosave" capability to save working files every 30 - 60 seconds. Perhaps that is something that would work?  

IMHO, this is a philosophical difference between Unix-like OSes and the other ones. In the Unix-world, the computer does what it is told, doesn't ask for permission, and not necessarily what the end-user "thinks" he has told it.

Oddly, I did find where people didn't want any confirmations - those solutions may be of help, but I doubt it: 
[https://askubuntu.com/questions/14794/how-do-i-shut-down-without-the-confirmation-prompt](https://askubuntu.com/questions/14794/how-do-i-shut-down-without-the-confirmation-prompt)

I'm firmly in the "don't ask me to do what I already told you to do" camp, but I can see where having each program capture the close-event would be helpful. The architecture of Unix and X/Windows can make what you seek possible, but the issue of having a system lock up over an end-user program bad behavior is a real concern.  The the program isn't responding, the OS needs to kill it, period.  How much time should the OS wait for X11 to ask every running program to close?  What happens when 20 of them are waiting for user-input, like the filename to be saved?  These are questions to be answered.  Seems possible to accomplish, at least within a single project like Gnome or LibreOffice or KDE. Don't know if other individual programs will follow or not.

Interesting idea.

---

