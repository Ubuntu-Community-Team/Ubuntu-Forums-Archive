---
title: "Bash, Mail on Error Only?"
date: 2009-04-11
forum: General Help
---

### Post by codeseer on 2009-04-11
I am working on a simple bash script. All it has in it is a few _rsync_ commands for backing up some files. I want to be mailed by the script _only if an error occurs_. Is there any way of doing that?

---

### Post by defaultusername on 2009-04-12
codeseer,

rsync's returns 0 on success. The exit values and their definitions are explained in "man rsync". You could use some kind of conditional statement in combo with

> 
/usr/bin/mail "$to" << echo $?


Of course, you would want to do some additional formatting as $? only returns the exit value of the last command (an integer). Anyway, that seems to be it in a nutshell.

---

### Post by codeseer on 2009-04-12
Seems like I need to actually learn 'bash'. I think I get what you're saying. I could essentially do this:

```

rsync something --log-file=/tmp/rsync_errors.log

if $? != 0

cat /tmp/rsync_errors.log | mail -s "Errors Occured in Rsync" root@localhost

fi


```

That's part pseudo, because I don't know what the comparison operators are. I'm also not sure about the 'if statement' content. Perhaps someone could correct it for me? ..or verify that I'm on the right path.

---

### Post by codeseer on 2009-04-12
I figured out the error detection part:

```

rsync something --log-file=/tmp/rsync_errors.log

if [ "$?" -ne "0" ]; then

cat /tmp/rsync_errors.log | mail -s "Errors Occured in Rsync" username@localhost

fi

```

Does anybody know of a 'cleaner' method to do this?

---

### Post by shel-hall on 2009-04-12
> **codeseer said:**
> I figured out the error detection part:

```

rsync something --log-file=/tmp/rsync_errors.log

if [ "$?" -ne "0" ]; then

cat /tmp/rsync_errors.log | mail -s "Errors Occured in Rsync" username@localhost

fi

```

Does anybody know of a 'cleaner' method to do this?
That's actually clean and readable, if it's the only instance of the code.  You could, of course, exploit the fact that *nix progras generally return "true" on success and "false" on failure, and ...

```

rsync something --log-file=/tmp/rsync_errors.log ||    \
mail -s "Errors Occured in Rsync" username@localhost < \
/tmp/rsync_errors.log

```
... which is really all one line; the backslashes mean that the CR immediately following is not the end of the logical line, only the end of the physical line.

However, since you probably don't want to write that code, or any code, over and over, once for each file you're going to transfer, you ought to look into various looping constructs.  It would be easy enough to have your script read from a text file the list of files to be transferred; this would mean you'd only need one instance of the file transfer and error checking logic.

I expect Heiner has a good example at  [http://www.shelldorado.com](http://www.shelldorado.com) somewhere.

-Shel

---

### Post by codeseer on 2009-04-12
Thank you both greatly for the help. I've learned quite a bit today. What I have now is:

```

BACKUPLOG="/tmp/backup.log"

rm -f $BACKUPLOG

function checkforerrors {

if [ "$?" -ne "0" ]; then
cat $BACKUPLOG | mail -s 'Backup Error' user@localhost
fi

}

rsync something --log-file=$BACKUPLOG something something; checkforerrors
rsync something --log-file=$BACKUPLOG something something; checkforerrors
...

```

---

