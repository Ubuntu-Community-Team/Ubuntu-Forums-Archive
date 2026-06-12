---
title: "Adept won't open!"
date: 2006-04-28
forum: Desktop Environments
---

### Post by link141 on 2006-04-28
I've just made the stupid mistake of adding some repositories incorrectly to adept and it won't open.  It prompts me for my password, and when I enter it correctly it jumps to an error message that says it couldn't open the APT Database.  Here is the exact message: 

"Could not open cache - Adept

The APT Database could not be opened! This may be caused by incorrect APT configuration or something similar. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

I take it this serious, being that the normally emotionless error message, in this case, has an exclamation mark after the first sentence.  
     I tried running the apt-setup command, and an interface prompted me for the Kubuntu install CD.  It wasn't able to detect it.  I tried running the apt-get update command in konsole as well, and it gave me yet another error.  I even tried installing synaptic from konsole and it gave me yet another error.
     Is there an easy way to fix this problem?  As of right now, I'm a moron when it comes to command prompts. 
Thanks. :)

---

### Post by Ensnared on 2006-04-28
If apt-setup looks for the CD, you probably still have it in your repositories from the install. If you're connected to the internet you have no use for that, so first step is to remove it.

Open a console and do this:```
sudo nano -w /etc/apt/sources.list
```This will open the sources.list-file in a simple text-editor called "nano". If you prefer a graphical editor, open the file with kwrite or kedit instead:```
kdesu kedit /etc/apt/sources.list
```or```
kdesu kwrite /etc/apt/sources.list
```
Note: Always use kdesu (or gksudo for Gnome) to run a graphical application with root privileges, but sudo to run a command-line/console command or application with root privileges.

Look for a line that starts with "deb cdrom:", and add a # in front of it. Chances are it's at the very top of the file, and it should only be one such line, but if you find several, comment them all out by adding a # in front of them (only if they start with "deb cdrom:" - leave the rest alone ;))

Close and exit - if you're using nano you do this by holding ctrl and pressing x, then y (for yes to save changes) and enter to save to the suggested location (which is the one you opened).

Then run```
sudo apt-setup
```and/or```
sudo apt-get update
```.

If you get any errors, post them here - we'll have this fixed in no time ;)

---

### Post by link141 on 2006-04-28
Thanks.  I will try this after I eat dinner (I know it's late) and post any problems I run into.

---

### Post by link141 on 2006-04-29
Thank you so much :D!   I opened the file with nano and removed the garbaged repositories by backspacing them out.  Adept opened right up without any errors!  In fixing this problem, you also answered my other question of how to open apps with root privileges.  Thanks! :D

---

### Post by bluecookies on 2006-05-07
i have same problem with adept : the database apt could not be open......

this is content of my source.list :

> 

#
# deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Beta i386 (20060420)]/ dapper main re
stricted

deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Beta i386 (20060420)]/ dapper main rest
ricted

deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security



which line should i add # ? 
i had added # at the first line "deb-cdrom" but it's not working, the adept still won't open and still with the same error

help me :sad: 

thanks

---

### Post by lowey23 on 2006-05-08
Hi bluecookies

Add the # before any line that has deb cdrom in it.

Should do the trick for you.

Cheers

Lowey

---

### Post by Ensnared on 2006-05-08
Looks like you got some linebreaking funkiness going on there. If you have any lines that actually begin with "stricted" or "ricted" (or anything similar), make sure to move them onto the end of the previous line.

This sort of things can happen if you use an editor like nano without using the -w switch, as that'll make it wrap long lines, which is a very bad thing when editing any kind of configuration-file. Not sure if the same applies to graphical editors, but it's generally a good idea to disable all kinds of word-wrapping when editing config-files.

---

### Post by link141 on 2006-05-08
Apparently, the Package managers are very sensitive to even the slightest error in the repository file.  That's the way it is with any program if it isn't told to ignore bad lines.  It seems strange though that no one thought tell it to ignore bad repositories  with the package mangers.

---

### Post by Furrybeagle on 2006-05-09
Getting the exact same error. I commented the line out of my sources.list, but then when I run sudo apt-setup it tells me command not found. When I run sudo apt-get update it tells me

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Didn't find "apt-setup" in /usr/bin or /usr/sbin. It's a fresh install so I'm not really sure what the issue is as I haven't really done anything to it.

---

### Post by link141 on 2006-05-09
A lot of the sudo commands don't work on my computer either :), and it gives me errors just like yours all the time.  That is the exact reason why I avoid the command line to run functions like this, and stick to the package managers.  In fact, all I did was remove or comment out the bad repositories, and open Adept.  Adept then worked fine without any errors.  
As for your errors, (I am no expert at this, it's a wild guess), the first one probably means that the database of the repository you were trying to get to, couldn't establish a database lock to prevent other users from editing the base while you were using it (that is probably no where near what it means :)).  And the second one almost certainly means that something else is running with root privileges, adept, system settings, even another terminal window, and countless other situations can cause this error, (usually only when they are open).  Just fix the repositories and run Adept as usual.  Hope that helps :).

---

