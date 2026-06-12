---
title: "Permission? - unable to chg root to user"
date: 2009-04-12
forum: General Help
---

### Post by hawkhock on 2009-04-12
Somehow my File System folder became locked as root.  In terminal I've tried

sudo chown -R georgi:georgi /georgi/File System

I also tried the path /home/File System; using lower case and no spaces. Same result is all efforts: chown can't access "File" nor "System" - no such file or directory. Or maybe I am not using the correct path.  When I open /home, the screen opens /georgi and there are two folders listed a)Home and b)File System.  

1)  In a forum, I read that having the File System folder locked is a good thing. Prevents noobs like me from possible disaster. BUT, does the lock on the folder prevent package upgrades?  If I clean house using "autoremove", will the lock on the folder prevent unnecessary files from being removed?

2)  What am I doing wrong in trying to change the permission from root to user for the File System folder?

Georgi

---

### Post by drs305 on 2009-04-12
First, stop doing this and don't do it again. I'll expand this in a minute.

A few minutes of typing later:

Okay, now that I have your attention. The reason your attempts to chown File System is that "File System" isn't really a folder. If it *was*, since it has a space, you would have to include it in quotes, "File System". If you click on *File System* in a file browser you will see that it is a designation for /, although it doesn't go by the "File System" name anywhere but in your browser.

Now, you don't want to be changing system file ownership from root to yourself. If you do, you will end up having to reinstall your system. The system folders are not meant to be altered by a regular user. Many of them will break if you change the owner from root.

Most of the configuration files a user might want to change are located in hidden files located in your /home folder (often designated as ~/ or $HOME). These folders contain the configuration settings for each individual user and can be changed by them with no special effort. If you can't see these folders in a file browser, CTRL-H usually will enable the viewing of hidden folders.

If you have to gain access to a system file, you do it with "sudo" combined with a command line entry, or "gksudo" with a graphical app.

The lock will not stop installations. When you install something, you will either include "sudo" in the command line or have to enter your password to install the app. This allows modification of the necessary system files *by the system installer*.


Here is the community documentation on using "sudo":
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by paradigm2 on 2009-04-12
> **hawkhock said:**
> Somehow my File System folder became locked as root.  In terminal I've tried

sudo chown -R georgi:georgi /georgi/File System

I also tried the path /home/File System; using lower case and no spaces. Same result is all efforts: chown can't access "File" nor "System" - no such file or directory. Or maybe I am not using the correct path.  When I open /home, the screen opens /georgi and there are two folders listed a)Home and b)File System.  

1)  In a forum, I read that having the File System folder locked is a good thing. Prevents noobs like me from possible disaster. BUT, does the lock on the folder prevent package upgrades?  If I clean house using "autoremove", will the lock on the folder prevent unnecessary files from being removed?

2)  What am I doing wrong in trying to change the permission from root to user for the File System folder?

Georgi

Hmm try:

```

sudo chown -R georgi:georgi "/georgi/File System"

```

If that does not work, try:

```

sudo chown -R georgi:georgi '/georgi/File System'

```

(I forget which is proper.)  It looks as if the main issue is the space, so it sees it as two files (neither of which exists), as opposed to the one which does exist.

edit:

Hmmm.  And usually home folders are stored under /home like so: "/home/georgi"

...but try the above and report what happens.

---

### Post by hawkhock on 2009-04-12
> **paradigm2 said:**
> Hmm try:

```

sudo chown -R georgi:georgi "/georgi/File System"

```

If that does not work, try:

```

sudo chown -R georgi:georgi '/georgi/File System'

```

(I forget which is proper.)  It looks as if the main issue is the space, so it sees it as two files (neither of which exists), as opposed to the one which does exist.

edit:

Hmmm.  And usually home folders are stored under /home like so: "/home/georgi"

...but try the above and report what happens.


Following is response from terminal:

georgi@georgi-desktop:~$ sudo chown -R georgi:georgi "/georgi/File System"
[sudo] password for georgi: 
chown: cannot access `/georgi/File System': No such file or directory
georgi@georgi-desktop:~$ sudo chown -R georgi:georgi '/georgi/File System'
chown: cannot access `/georgi/File System': No such file or directory
georgi@georgi-desktop:~$

---

### Post by The Cog on 2009-04-12
It would help to be able to see exactly what you're looking at. Can you post a screenshot? Pressing PrintScrn should save one to the desktop. Don't try changing anything until people have had a chance to understand what you're looking at. I suspect it's something that shouldn't be changed anyway.

---

### Post by hawkhock on 2009-04-12
> **drs305 said:**
> First, stop doing this and don't do it again. I'll expand this in a minute.

A few minutes of typing later:

Okay, now that I have your attention. The reason your attempts to chown File System is that "File System" isn't really a folder. If it *was*, since it has a space, you would have to include it in quotes, "File System". If you click on *File System* in a file browser you will see that it is a designation for /, although it doesn't go by the "File System" name anywhere but in your browser.

Now, you don't want to be changing system file ownership from root to yourself. If you do, you will end up having to reinstall your system. The system folders are not meant to be altered by a regular user. Many of them will break if you change the owner from root.

Most of the configuration files a user might want to change are located in hidden files located in your /home folder (often designated as ~/ or $HOME). These folders contain the configuration settings for each individual user and can be changed by them with no special effort. If you can't see these folders in a file browser, CTRL-H usually will enable the viewing of hidden folders.

If you have to gain access to a system file, you do it with "sudo" combined with a command line entry, or "gksudo" with a graphical app.

The lock will not stop installations. When you install something, you will either include "sudo" in the command line or have to enter your password to install the app. This allows modification of the necessary system files *by the system installer*.


Here is the community documentation on using "sudo":
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Sorry - I read the last entry first - will stop trying to change the permissions.  Since I started using Linux, the File System folder has never been locked. Therefore I thought it should be unlocked. Still don't understand how it was unlocked one day and locked the next.  Probably something I did that I am unaware of.  Thanks for help.
Georgi

---

### Post by paradigm2 on 2009-04-12
> **hawkhock said:**
> Following is response from terminal:

georgi@georgi-desktop:~$ sudo chown -R georgi:georgi "/georgi/File System"
[sudo] password for georgi: 
chown: cannot access `/georgi/File System': No such file or directory
georgi@georgi-desktop:~$ sudo chown -R georgi:georgi '/georgi/File System'
chown: cannot access `/georgi/File System': No such file or directory
georgi@georgi-desktop:~$

Looks like drs305 is probably correct then. :)  Definitely read that.

"Home" - means a users "home" directory.  Your home is probably /home/georgi for example.

"File System" - means the root (beginning/main) part of your disk.  Typically this is actually "/".

drs305 is correct, you do not want to make your filesystem owned by yourself.  Be careful.  It should remain owned by "root"

I thought you actually had a separate directory called "File System" within /home/georgi/ but you do not.

---

### Post by drs305 on 2009-04-12
I think now that the dust has settled and we know you aren't trying to change ownership of / you can take the advice of *The Cog* in post #5 and give us better information to work with. 

You *should* be able to click on "File System" and see your other files. We just need a clearer picture of exactly what happened.

---

### Post by Penguin Guy on 2009-04-12
There shouldn't be any such file as "georgi/File System" the name of the filesystem is "/". Most of the folders in the filesystem are *meant* to be locked - do not try to unlock them. If you want to temporarily be able to modify them then press Alt+F2 and type [COLOR="DimGray"]gksu nautilus[/COLOR]. However that is extremely inadvisable until you have more experience with Linux.

---

### Post by hawkhock on 2009-04-12
Thanks to all for your willingness to help. I sure do miss the Thank You button. Not sure what I did where but could not access terminal or much of anything else.  Had to do a clean install. I back up my /home files once a week and all my personal files are current so except for the aggravation I'm okay.

Funny thing is that the clean install does not have a locked File System icon yet all the individual file system folders are locked as root. So still not sure what caused the locked icon to begin with but it is a moot point now.  In the meantime, between forum research and you all, I learned a lot.  Consider this thread SOLVED.

Georgi

---

