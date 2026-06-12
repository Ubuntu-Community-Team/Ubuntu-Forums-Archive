---
title: "New to Ubuntu, familiar with Linux, have prob."
date: 2005-11-25
forum: Desktop Environments
---

### Post by Blizkreig75 on 2005-11-25
Hello, everyone! I'd like to begin by setting the ground for the support I hope to receive by telling you a bit about my computing setup.

I build PCs. I have three or four computers at any given time, (there's always a "tester" unit), all running different OS's,(XP Pro, Mepis, Slackware 10.2, and Ubuntu 5.10). I've use Mepis the most of all my Linux distros, but really like how smooth this Ubuntu runs. 

I noticed that when I installed Ubuntu I did not get promted to enter a root password and now I'm performing an operation that requires me to be the root. 

How do I change the root password?

---

### Post by Leif on 2005-11-25
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Blizkreig75 on 2005-11-25
When I input my user password, "access denied". According to that link, my user password should work, but it doesn't.

Will enableing root seriously cripple the OS operating the GUI properly?

EDIT: I'm doing this from a command line when this occurs.

---

### Post by earobinson on 2005-11-25
you should be able to search the forums to find the answer to this question I searched for (root password) and I found this

[http://www.ubuntuforums.org/showthread.php?t=94520&highlight=root+password](http://www.ubuntuforums.org/showthread.php?t=94520&highlight=root+password)
> The normal installation:
u do sudo su
from the user (at installation)
then, passwd
enter the root password
and that's it !

sudo su
[enter password]
psswd

will do fix it for you. (I use a root password and have had no problems)

---

### Post by Blizkreig75 on 2005-11-25
[QUOTE=earobinson
sudo su
[enter password]
psswd

will do fix it for you. (I use a root password and have had no problems)[/QUOTE]
Alright. that worked.

Now, I've found that I need to edit two files in order to get the build to work. I found a wiki that says I need to "remove the big comments at the top". What exactly am I looking for? I'm not familiar with the term "comments", unless thay're talking about actual comments from the programmer.

---

### Post by earobinson on 2005-11-25
Im not sure I under stand your question what is the "build" you are speaking of? can you link to the wiki you are talking about

---

### Post by Blizkreig75 on 2005-11-25
I'm trying to get CVSCedega running. Here's the wiki:
[http://wiki.archlinux.org/index.php/Cvscedega](http://wiki.archlinux.org/index.php/Cvscedega)

The how-to is:
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

---

### Post by Blizkreig75 on 2005-11-25
Anyone at all........

---

### Post by llbbl on 2005-11-25
I reinstalled ubuntu thinking I mistyped the root password or something because everytime I tried to su it didn't work and then i $vi /etc/passwd and there was root so I screwed up something during install. /sigh damn sudo :)

---

### Post by Drain on 2005-11-25
[QUOTE=Blizkreig75]Alright. that worked.

Now, I've found that I need to edit two files in order to get the build to work. I found a wiki that says I need to "remove the big comments at the top". What exactly am I looking for? I'm not familiar with the term "comments", unless thay're talking about actual comments from the programmer.[/QUOTE]

If I understand the directions correctly (and who know, I might not!) they want you to delete the comments of the two files. Open up a text editor, and delete all the lines that start with a "#" sign.

---

### Post by Leif on 2005-11-26
[QUOTE=Drain]If I understand the directions correctly (and who know, I might not!) they want you to delete the comments of the two files. Open up a text editor, and delete all the lines that start with a "#" sign.[/QUOTE]

I don't think that's right - I think it means he should delete just the #s in lines beginning with them.

---

### Post by stalefries on 2005-11-26
Instead of having a root user, the Ubuntu developers decided to force the user to use "sudo" before each command the requires root privileges. The have a bunch of reasons for this, and I don't want to get into it, but you could easily find this on Google.

---

### Post by YanH on 2005-11-26
An easy way of becoming the root user without changing any config files is to use the sudo command to switch user.

sudo su -

And then enter your user password.

---

