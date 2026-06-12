---
title: "PATH Variable Issues"
date: 2005-02-22
forum: Desktop Environments
---

### Post by cybane on 2005-02-22
After some searching I had been told that if I want to be able to run the mysql command from anywhere in the filesystem I would need to change the PATH= line in the /etc/profiles.

I did that and added the proper line of:
PATH="/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11:/usr/games:/usr/local/mysql/bin"

Now here is my problem.  After I restarted my machine (I know it is not required but meh) I did the echo $PATH.  This returned the result of:
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

However, the desired result was:
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/usr/local/mysql/bin

Now after I modfied my .bashrc file with this line:
export PATH=${PATH}:/usr/local/mysql/bin
I get the desired result.

I was told that all I would have to do is modify the /etc/profiles to make this change globaly except for root.

Did I do something wrong.  I know the problem is solved but it is only solved for me.  I would like that any person I make an account for to be able to use the mysql command from anywhere in the directory structure.

If you have any thoughts or possible solutions please let me know.  Also, if you know which files can change the $PATH for a user that would be good to know as well.

Thanks,
Cybane

---

