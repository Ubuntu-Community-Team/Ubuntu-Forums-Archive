---
title: "Oh Lord Please Help!"
date: 2006-02-20
forum: Desktop Environments
---

### Post by Cysman on 2006-02-20
Hi folks, I just did a stupid thing!  I completely messed up my permissions to log onto my computer.  The only way I can log on is the failsafe text mode.  It all started out when I was dinking around with the permissions on my home folder and now I can't connect to the free world now.  Please help!:cry:

---

### Post by dickohead on 2006-02-20
sudo chmod -R 755 /home/you
sudo chown -R you /home/you

---

### Post by Lord Illidan on 2006-02-20
```
 	Oh Lord Please Help!
```
You called? Ask and ye shall recieve.

Try this from failsafe:

```
sudo chown -R *your username* /home/*your username*
``` (remove asterisks)

---

### Post by Ramses de Norre on 2006-02-20
Your home folder should have the permissions drwxr-xr-x, you should be able to restore them from the recovery mode.
Or you can use the recovery mode to set a root password by using passwd root (recovery mode is a root console, isn't it? I never used it yet).
And then login as root ans restore the permissions.
I'd advice to unset the root password after doing that.

---

### Post by GTvulse on 2006-02-20
[QUOTE=dickohead]sudo chmod -R 755 /home/you
[/QUOTE]

That's completely unnecessary and, in fact, outright dangerous. You are making each and every single file executable. 

And by the way, the default directory permissions for home directories in Ubuntu are 0700, that is: ```
sudo chown 0700 /home/you
``` will restore the original defaults.

---

### Post by Cysman on 2006-02-20
[QUOTE=dradul]That's completely unnecessary and, in fact, outright dangerous. You are making each and every single file executable. 

And by the way, the default directory permissions for home directories in Ubuntu are 0700, that is: ```
sudo chown 0700 /home/you
``` will restore the original defaults.[/QUOTE]

Ok, well thankfully I'm back on now.  Now what should the permissions be again for home?  And please......draw it out in crayon for me...I don't ever want to do that again;)

---

### Post by Cysman on 2006-02-20
Getting back to your responce, I typed in those commands given by dickohead and it worked.  I looked on the permissions of my home folder and they do say exactly what you posted.  So is it good to go?  If it is, I promise to never touch that again!!!!

---

### Post by dickohead on 2006-02-20
as dradul pointed out, the permissions would be better off being 744, my apologies so used to setting permissions for apache and samba!

so if you type the following:

sudo chmod -R 744 /home/you
all files and folders under /home/you will be readable by everyone, but writeable by you, if you want to make it very secure so only you have access type this:

sudo chmod -R 700 /home/you

Good luck.

---

### Post by dickohead on 2006-02-20
Just try logging in again, if it doesn't work we'll take it from there. But if you were playing with permissions and then it died, chances are very good that one of the files used by gnome was not readable/executable or writeable to gnome, so you would have received an error or a lock up.

I've done it HUNDREDS of times! But as long as you remember that:

**chmod** - changes the permissions of files/folders

777 is full RWX for everyone: drwxrwxrwx
744 is read and execute for everyone, full for you: drwxr_xr_x
700 is no access to anyone but you: drwx______

**chown** - changes the owner of the files/folders
**chgrp** - changes the group of the files/folders

-R tells the command to go recursively down into all folders, without the -R it only changes the top folder.

---

### Post by eltaito on 2006-03-07
I would just like to say thanks....I was screwing around with impunity as usual and had the same problem.....changing the permissions as stated worked like a charm....thanks guys

---

