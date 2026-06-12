---
title: "scripting backup over ftp"
date: 2005-03-21
forum: Desktop Environments
---

### Post by cruzlee on 2005-03-21
I know it can be done, but because I am a total newbie to linux i do not know how.

Let's say the location and name of the file that needs to be backed up is:
\home\kitchen\list.txt

the ftp server's adress is:
ftp.tralala.org

username and password are
ftp / trala

how should I write such a script? Can you give commands to an ftp client with scripting?

---

### Post by alastair on 2005-03-21
Perl or Python? In Perl, you could :

e.g. from "perldoc Net::FTP :

```

use Net::FTP;
$ftp = Net::FTP->new("some.host.name", Debug => 0)
      or die "Cannot connect to some.host.name: $@";
$ftp->login("anonymous",'-anonymous@')
      or die "Cannot login ", $ftp->message;
$ftp->cwd("/pub")
      or die "Cannot change working directory ", $ftp->message;
$ftp->get("that.file")
      or die "get failed ", $ftp->message;
$ftp->quit;
```

---

### Post by cruzlee on 2005-03-21
I was thinking of a bash script? (isn't that the linux alternative to a .bat file, a batch?)

---

### Post by alastair on 2005-03-21
Yes, a bash script is equivalent to DOS .bat files - but WAY superior (no comparison really).

However - remember that FTP is an interactive command. It expect you to input things, and act at a prompt. This is hard to script - BUT, you can use something like "expect" - see :

[http://expect.nist.gov/](http://expect.nist.gov/)

and also perhaps :

[http://www.users.qwest.net/~eballen1/scripting.ftp.html](http://www.users.qwest.net/~eballen1/scripting.ftp.html)

---

### Post by az on 2005-03-21
Are you doing this from inside your lan or from anywhere?  Because there are more secure ways of doing this kind of thing.

---

### Post by WW on 2005-03-21
If the server at ftp.tralala.org has an ssh server running, you could use scp.
Something like this might work:```
 $ scp /home/kitchen/list.txt ftp@ftp.tralala.org:list.txt
```You could put the scp command in a file called "listbackup.sh", and run it with the command ```
 $ sh listbackup.sh
```

---

### Post by cruzlee on 2005-03-21
Security is not **really** important, because the data that gets transmitted is not critical. I got as far as writing a bash script that uploads the file to a ftp. Also I put this script in crontab and this works too. Furthermore, sftp is supported by the remote site, i will look into this when the rest is done.

There's some tuning left to do, but I already figured out that if you don't like 'reading the fine manuals' linux is not for you anyway. Thank you guys for your help.

[I](what's left to do:

- kitchencomputer needs to create a dir with name like this on ftp:
"/20050322" on 22 march 2005 and put the files there. 

- after a month, every dir except the first one of each month (*01)
has to be deleted.)

ideas?
[/I]

---

### Post by dare2dreamer on 2006-08-03
lftp, which is in the repositories, allows for scripted sessions.

---

