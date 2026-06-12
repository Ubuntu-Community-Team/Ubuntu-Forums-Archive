---
title: "Can't install anything, please help"
date: 2006-05-04
forum: Desktop Environments
---

### Post by harobmx050 on 2006-05-04
I'm very new to ubuntu lik two days ago new... anyway, when i go to "add applications" in the applications pull down, it asks for a password and then i enter it and it says "unable to get lock" and right under it it says "This usually means that another package management application "like apt-get or aptitude" already running.  Please close that application first."  If anyone could help, i dunno if i gave enough information or not, but any assistance is appreciated.

---

### Post by matthewstory on 2006-05-04
open a command line terminal:

Applications > Accessories > Terminal

type in the following line:

ps aux | grep apt

Copy and paste the result (SHFT-CTRL-C) and post it back up here.

---

### Post by harobmx050 on 2006-05-04
spud     10985  0.0  0.1   3060   756 pts/0    S+   16:55   0:00 grep apt

---

### Post by matthewstory on 2006-05-04
Are you using Synaptic, right now i'm on  a Debian box, so I don't know if what you're describing is the Synaptic package manager, but if you're not using the Synaptic package manager, then you should be.  (btw the result shows that aptitude and apt-get aren't running).  I think its in:

Admin > Synaptic

but not totally sure.  Otherwise you can manually install stuff using apt-get:

open terminal again:

To find the package:

sudo apt-get search <what you're looking for>

Then to install

sudo apt-get install <package name>

to uninstall

sudo apt-get remove <package name>

etc.

---

### Post by harobmx050 on 2006-05-04
i am using synaptic package manager, the only problem is i don't know how to use it, lol cuz i just started linux

---

### Post by harobmx050 on 2006-05-04
when i go to search it says 
bash: syntax error near unexpected token `newline'
and also when i go to install i enter in the directory of where it's located and it just goes to next line and i guess it's waiting for further commands, and it doesn't do anything...

---

### Post by matthewstory on 2006-05-04
just to see if apt-get is working properly without the synaptic on top of it run the following test (in the command line):

sudo apt-get update
sudo apt-get search debsums
sudo apt-get install debsums
sudo apt-get show debsums
sudo apt-get purge debsums

The first line updates the local apt database
the second one searches for the program debsums, you should get one result (this is a security program) the third line installs the program, and the fourth line shows the status and description of the package (it should say installed under state near the top of the print out), and the fifth line removes the package.  If you get errors on this post them here, if not you probably just had a syntax error on the last time, and there's probably something wrong with synaptic and we can reinstall it.  However if apt-get is screwed up we have alot more work on our hands.

---

### Post by harobmx050 on 2006-05-04
spud@shanker:~$ sudo apt-get search debsums
E: Invalid operation search

that's what i got when i tried to search so i wasn't able to make it to the third command line

---

### Post by matthewstory on 2006-05-04
oops, sorry search and show are only options for aptitude, appologies, just run this:

apt-get update
apt-get install debsums

at this point if there are no errors it should be installed, if you can't tell that its install then check by trying to open the man page:

man debsums

to exit this page hit q, if no page showed up than the install failed.

now remove it

apt-get remove debsums

and then try the man page again, it shouldn't work now.  Any errors post them here again.

---

### Post by harobmx050 on 2006-05-04
there's gotta be something wrong... :(

spud@shanker:~$ apt-get update
E: Opening /etc/apt/sources.list - ifstream::ifstream (13 Permission denied)
spud@shanker:~$ apt-get install debsums
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

btw you wouldn't happen to have an AIM s/n so that we can talk thru there would u?

---

### Post by matthewstory on 2006-05-04
no, not quite yet here's the problem you've got to put sudo in front of the apt-get commands . . . my bad:

sudo apt-get update
sudo apt-get install debsums
man debsums

(hit q to exit)

sudo apt-get remove debsums
man debsums

sorry about that.  If you have a google account feel free to google talk with me:

matthewstory is my screen name

---

### Post by matthewstory on 2006-05-04
yes I have an AIM account as well, just logged on CodeWarrior16

---

