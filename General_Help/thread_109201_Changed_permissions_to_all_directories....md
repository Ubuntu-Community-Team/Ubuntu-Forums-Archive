---
title: "Changed permissions to all directories..."
date: 2005-12-28
forum: General Help
---

### Post by mortong on 2005-12-28
I've recently switched to KDE from Gnome.  The new terminal program that runs in KDE has some different rules than I'm used to.  In Gnome, to change permissions on multiple files in my home dir, I'd:

cd ../..
cd home/[user name]
sudo chmod 770 */*/*/*... etc. as far as i need to go, and it only changed the permissions on files within subdirs under my home directory.

With KDE, /*/ made it so that ALL directories in the file system were set for 770.  This means I can no longer run sudo, and am having some other problems.

Can anyone give me some advice on how to fix/restore system files without losing my home dir, without reinstalling everything?  Thanks.

---

### Post by Nate53085 on 2005-12-28
the problem is in your syntax

*/*/ is not the same as /*/*

 regrettably, I have no idea what to do to fix that.

---

### Post by HermanAB on 2005-12-28
Ugh...  Re-install will be the easiest way to fix this mess.  If your home dir is a separate partition, then you can preserve it - just don't format it during the install.  If it isn't a separate partition then you have now learned why it should be... :)

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by mortong on 2005-12-28
[QUOTE=Nate53085]the problem is in your syntax

*/*/ is not the same as /*/*

 regrettably, I have no idea what to do to fix that.[/QUOTE]

Sorry, that was lazy typing on my part.  Here's the exact cut and paste:

sudo chmod 777 /*/*  (this was done from within /home/mortong/)

I didn't realize there would be this sort of difference between KDE and Gnone in the terminals.  Grrr, I don't want to re-install, but I can back everything up.  I will definately create a partition for my home dir in the future.  Thanks for the replies.

I've played around with the install cd, and one thing I can't find is a repair option.  That's one thing I miss about Fedora (but that's about the only thing). :p

---

### Post by Nate53085 on 2005-12-28
no, /*/* references not from your home directory.  This would have acted the same in Gnome or KDE, the difference is whether or not you started with a / or a *.

A / would have started from your root directory
A * would have started from your working directory (which I assume was Home for the situation you were talking about)

---

### Post by mortong on 2005-12-28
[QUOTE=Nate53085]no, /*/* references not from your home directory.  This would have acted the same in Gnome or KDE, the difference is whether or not you started with a / or a *.

A / would have started from your root directory
A * would have started from your working directory (which I assume was Home for the situation you were talking about)[/QUOTE]

That explains my mistake.  Thanks for clarifying that.  I know what NOT to do from now on.  Now to backup and start a fresh install. :rolleyes:

---

### Post by mortong on 2005-12-28
Done.  I've got some work to do to finish updating, installing, etc., but I've got a fresh install and a separate partition for my home dir (it's currently holding my entire previous install, so there was no loss).

Thanks for your help.


[QUOTE=HermanAB]Ugh...  Re-install will be the easiest way to fix this mess.  If your home dir is a separate partition, then you can preserve it - just don't format it during the install.  If it isn't a separate partition then you have now learned why it should be... :)

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)[/QUOTE]

---

### Post by lcg on 2005-12-28
[QUOTE=mortong]In Gnome, to change permissions on multiple files in my home dir, I'd:

cd ../..
cd home/<user name>
sudo chmod 770 */*/*/*... etc. as far as i need to go, and it only changed the permissions on files within subdirs under my home directory.[/QUOTE]
First of all, if you're changing permissions in you own home, you can achieve the same with
```
cd ~
chmod 770 * -R
```
Notice that I don't chmod as root via sudo. That was the mistake that's causing you trouble now. The files in your home are usually owned by your user, so you can chmod them without being root. However, as root, you had the right to change the permissions all over the filesystem, starting from /.

You have just learned the reasons why doing everyday work as root is a bad idea. As a rule of thumb, people should always work with the least priviliges possible, it saves them from their own stupidity.

HTH,
Lars

---

### Post by farfargoth on 2005-12-28
Just a question that may be a bit OT, but it looks like a mistake I did earlier...
 if you did
```
sudo chmod 770 */*/*
``` 
wouldn't that also change the permission of all files to 770?
Since .. and . also is a directory.. That means that if you do it in /home/user/ then it would chmod /home/user/../../* as well (wich is equal to /*). That means he would get the same result the first and the second time. 
I accidentally did this with rm -rf on one of the schools computers when I had root access...:( That kind of sucked... Just a fair warning...

---

### Post by Refrozen on 2005-12-28
I have done this before, what I did to repair it was look at a default install, and recreate those [permissions](http://manlib.com/man/166).

---

### Post by Refrozen on 2005-12-28
Also, becareful when [using sudo](http://manlib.com/man/1118), only use it when you absolutely need it, and think about it before doing so!

---

### Post by hillbilly on 2006-01-05
I know this is an old thread. But just for curiositys sake, wouldnt you have been able to login as root user and fix this problem ??

---

