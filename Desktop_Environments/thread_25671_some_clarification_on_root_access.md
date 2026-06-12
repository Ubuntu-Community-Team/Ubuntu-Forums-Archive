---
title: "some clarification on root access"
date: 2005-04-10
forum: Desktop Environments
---

### Post by denzilla on 2005-04-10
Hi,

You're favorite dumb@ss here with another question. To clarify gaining root access to a folder in order to make modifiactions, this is what I understand it to be:

1. open the terminal and change directory to the desired location.

cd /usr/share/wallpapers

2. Once I have terminal in the right location, I type

su root

enter password

Okay, at this point I see the $ sign has been replaced with a # sign which I guess means I now have root access to that dir. Now, I try to copy a file to the wallpapers directory but it still says I don't have permission to do so. What am I missing here?

---

### Post by kkathman on 2005-04-10
What you are missing is a major point in Ubuntu, that being there is no real root user.

For your "root" operations, just precede them with the command "sudo".

so to execute a copy as root you would type:

sudo cp /thisdirectory/thisfile  /thatdirectory/thatfile

As for not having priviledges, if you dont execute under root, then as a regular user (i.e. a $ user) you cant write to some areas. If you want to write to certain directories as a non-root user, you need to change the permissions using chmod.

Example, say you want to copy a file to a wallpapers file. First you create the directory in say your home folder:

cd /home/yourname

sudo mkdir wallpapers

But because you created it with sudo, the wallpapers directory will have a restricted access to root only.  You change this by resetting its access to anyone can write to it:

sudo chmod 777 /home/yourname/wallpapers

Now anyone can write to that directory with no permission problem.

You can always check out the permissions by doing an ls -l   on that directory.

Hope this helps.

---

### Post by denzilla on 2005-04-10
Thanks, thats what I needed to know!   :-)

---

### Post by Jeffredo on 2005-04-10
I'm sure it's been hashed out many, many times since Ubuntu first appeared, but this  "no root", sudo user stuff is really tedious.  Mine is a single user, hardware firewalled PC.  I don't need all the security hand-holding and protecting me from myself.  I'm new to Linux (a couple months) and I much prefer Fedora Core's root/user set up at installation.  It warns you not to set up root as a user, but if you want to proceed, it allows to to make that choice.  If I royally screw something up, I can always reinstall.  In a business setting I can absolutely see the need to it, but for home users, again, all the sudo this and that and password typing is a bit of a pain.

---

### Post by dewey on 2005-04-10
If you prefer to have a root account, do it.
```
$sudo password
```
```
$su -
```
And use the su password you just created.
And you have a fully functional root account.

---

### Post by LusiphurScyla on 2005-04-11
and what if a putted a fake password? i mean one i cant remember? im done? no chances but re-install...or not?

---

### Post by abovett on 2005-04-11
[QUOTE=LusiphurScyla]and what if a putted a fake password? i mean one i cant remember? im done? no chances but re-install...or not?[/QUOTE]

There are ways of recovering from a lost root password - do you have this problem, or is this just a "what if"? If you need help let me know.

Not sure why people find the "no root password" thing a problem though. I almost never log in directly as root even on distros that allow it by default - I log in as a normal user and SU to root when I need a root prompt. sudo -s will do the same on Ubuntu as su does on other distros, and if that's too much to type you can always alias it to something shorter! The advantage of course is that you don't need to remember a second password - just re-supply your normal user password.

HTH

Andy B

---

### Post by antiphon on 2005-04-11
[QUOTE=LusiphurScyla]and what if a putted a fake password? i mean one i cant remember? im done? no chances but re-install...or not?[/QUOTE]
 You can always do  "sudo passwd" again. The old password is not required.

I like using real root access (using "su" or just logging in as root from tty's) when there
is more than one command  to execute. For installing packages, I use "wajig", which uses sudo automagically.

-tuomas

---

### Post by kal_zakath on 2005-04-11
If you want a root session is a terminal with sudo, just use the :
```

sudo -s

```
command

I use it all the time and it is really helpfull

---

### Post by procyon on 2005-04-25
[QUOTE=kkathman]What you are missing is a major point in Ubuntu, that being there is no real root user.

For your "root" operations, just precede them with the command "sudo".

so to execute a copy as root you would type:

sudo cp /thisdirectory/thisfile  /thatdirectory/thatfile

As for not having priviledges, if you dont execute under root, then as a regular user (i.e. a $ user) you cant write to some areas. If you want to write to certain directories as a non-root user, you need to change the permissions using chmod.

Example, say you want to copy a file to a wallpapers file. First you create the directory in say your home folder:

cd /home/yourname

sudo mkdir wallpapers

But because you created it with sudo, the wallpapers directory will have a restricted access to root only.  You change this by resetting its access to anyone can write to it:

sudo chmod 777 /home/yourname/wallpapers

Now anyone can write to that directory with no permission problem.

You can always check out the permissions by doing an ls -l   on that directory.

Hope this helps.[/QUOTE]

jusk want to ask how can i make the file back to restricted access to root? only

---

### Post by segrewb on 2005-04-25
chmod 755 should work.  For more info on what the numbers mean do a 'man chmod'

Segrewb

---

