---
title: "Desktop went blank..."
date: 2014-04-08
forum: Desktop Environments
---

### Post by w9wi on 2014-04-08
13.04.   I rebooted this morning & after logging into the GUI desktop, all I get is the background.  

There are no icons, there is no launch strip on the left, there is no status bar on top.  Right-clicking on the desktop gives the option of creating a blank document -- no other type of new document is available on the list.

Rebooting again has no effect.

I can open a terminal & navigate there just fine.  "top" doesn't show any unusual processes, nor anything using unusual amounts of resources.


What I was doing last...

I'd added a repository for a software-defined radio application. (gqrx)  Noticed the update notification icon on the top status bar had lit up -- and was saying some kind of error had happened looking for updates.  Removed the repository, didn't help.  Rebooted.

I did find a .config/compiz-1/compizconfig/unity.ini file that didn't exist at the time of my last backup about a week ago.  Renaming it to .in_ doesn't help.

sudo apt-get update returns no errors or updates.  

No apparent errors in Xorg.0.log.

---

### Post by w9wi on 2014-04-08
Solved my own problem, although I'm not sure why it worked...

I reinstalled Unity, (sudo apt-get install unity)  then rebooted.  


Clue: If I right-click on a desktop document, there's a new option at the top of the menu: Open With MonoDevelop.  Mono Development was part of the process for building an alternate software-defined radio application.  

(yep, I forgot to mention the critical step...  gotta love human memory...)

How that killed Unity I don't know, but it appears that it did.

---

### Post by Kevin McCready on 2014-04-11
I'm using Saucy Salamander and had the same problem. Installing Unity again didn't help.

Here's what caused the problem.
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-get update && sudo apt-get install skype
(got errors and skype didn't seem to install)
Any help would be appreciated.

---

