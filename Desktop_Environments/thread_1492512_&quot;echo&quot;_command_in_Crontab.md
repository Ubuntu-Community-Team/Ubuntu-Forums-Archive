---
title: "&quot;echo&quot; command in Crontab"
date: 2010-05-24
forum: Desktop Environments
---

### Post by Xafer on 2010-05-24
Hi there, I just setup a cron that display a message like : "hello world" for every minutes. So I put this:

* * * * * echo "hello world"

And then I waited and stare at terminal.
But seems like it doesnt shown off, did I messed up something?

---

### Post by Xafer on 2010-05-25
I also tried to put the echo command on some .sh script, so the crontab :

* * * * * sh test.sh

but still not working

---

### Post by a-user on 2010-05-25
as far as i know there is no way to do this. in fact echo is correct but there is no terminal output connected to the process when it gets executed. hence no output to be seen.

demons have no stdout and thus never can print messages. you may redirect the output to a file and look into that file.

try something like:
* * * * * echo "hello world" > /home/myuser/test.out

where myuser is your users name. but its probably better to put the exho command into a shell script file.

---

