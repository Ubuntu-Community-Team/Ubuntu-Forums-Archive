---
title: "Problem with shc encrypted shell script"
date: 2009-06-07
forum: General Help
---

### Post by MartijnNL on 2009-06-07
Hello,

I have created a shell script which automates some backup tasks. For security purposes I have encrypted it using shc.

On my own computer (32 bits xubuntu hardy) this runs just fine.

However, on another computer (64 bits xubuntu hardy) one particular command in the script doesn't work.

The command is basically:

```
ssh user@domain.com rm directory/*.*
```Now in the following cases it works fine (on this second computer):

[LIST=1]
[*]Using the terminal I ssh into the server manually and run "rm directory/*.*"
[*]I run the command above manually in the terminal
[*]I run the full unencrypted shell script
[/LIST]
However when I run the encrypted script, suddenly I get errors like:

> Cannot remove `directory/blabla.bla`: No such file or directorySo it does seem to see the files (otherwise it wouldn't be able to give the fill name) but when it tries to delete them, suddenly the files can't be found.

Any ideas to why this might occur?

Like I said, when I run the exact same encrypted shell scrypt on my own computer it works fine. It doesn't make a difference whether I compile the encrypted script on the other computer (although that does produce a warning message) or I compile it on my own with the -r option. In both cases it doesn't work properly on the other computer.

Any help would be appreciated.

Regards,

Martijn

---

### Post by blueridgedog on 2009-06-07
Have you tested it with a specific file to remove, rather than the wild card?  Based on your testing, it is down to the delete command, so the only further step is to see if it works if the file is specified.  It may help break down what part of the command is failing.  Also, do ANY files get deleted?

---

### Post by MartijnNL on 2009-06-07
> **blueridgedog said:**
> Have you tested it with a specific file to remove, rather than the wild card?  Based on your testing, it is down to the delete command, so the only further step is to see if it works if the file is specified.  It may help break down what part of the command is failing.  Also, do ANY files get deleted?

I have been testing some more and it turns our the problem has nothing to do with the script. But with the directory in which I am when the script is run.

The script is run from /home/foo
In this directory exits a subdir called backups, so this is
/home/foo/backups

When I run the command

ssh [email]user@domain.com[/email] rm backups/*.*

from /home/foo, it produces the error. The filenames it finds are not on the remote server but in the local directory /home/foo/backups.

So for some reason it looks at the local backup directory and then determins that it can't find the files on the remote system. Instead of just checking the remote directory.

If on the other hand I run the script from /home/bar, where no directory backups exists, I works fine.

This is kind of weird. But I just came up with a solution:

If I make the command

ssh [email]user@domain.com[/email] "rm backups/*.*"

so with quotes around it, it works fine.

So problem solved. Luckily. I spent hours on this.

Greetings

---

