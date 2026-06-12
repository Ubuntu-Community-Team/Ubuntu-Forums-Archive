---
title: "Bash Newbie --&gt; SSH commands through bash?"
date: 2009-05-10
forum: General Help
---

### Post by supergrover1981 on 2009-05-10
Hi gang,

I'm trying to automate some things, and thought I'd try my hand at a bash script. (New to bash)

What I'm trying to do is upload an sql file to the remote server, then log in via ssh, import the data through mysql & log out again.

Here's where I'm up to:
```

#!/bin/bash
HOST='MyHostIP'
USER='MyUserName'
PORT='MyPort'

scp -P $PORT /home/myaccount/Sandbox/sqlupdate.sql $USER@$HOST:/home/remotefolder/
ssh $USER@$HOST -p $PORT
mysql -u root --password=mypass
```

The problem I'm having is that having logged into ssh, other commands don't seem to process. That is, the 'mysql' line (or anything else once logged into ssh) won't process.

Is there a simple way to run ssh commands via bash? Any help much appreciated. :-)

Cheers,
        - JB

---

### Post by Peter09 on 2009-05-10
to run a command remotely using ssh at login do

```
ssh -X <username>@<remote machine> <command to run>
```

---

### Post by mb_webguy on 2009-05-10
Your problem is that ssh is an application.  The script calls it, then waits for it to terminate before running any other commands.  So the mysql command as you have it in your script will run on the local machine after you exit ssh.  You need to send a command to be executed via ssh (which conveniently takes a command as an argument).

Since you actually seem to want to execute more than one command, I'd suggest creating a script on the remote host with the commands to be executed.  Then you should be able to execute that script using ssh through the local script.  (It's really not as confusing as it sounds...)

So let's say you create a script on the remote host called "do_mysql_stuff".  Then your local script could be something like:```
#!/bin/bash
HOST='MyHostIP'
USER='MyUserName'
PORT='MyPort'

scp -P $PORT /home/myaccount/Sandbox/sqlupdate.sql $USER@$HOST:/home/remotefolder/
ssh $USER@$HOST -p $PORT do_mysql_stuff
```

---

### Post by supergrover1981 on 2009-05-10
Many thanks - exactly what I needed. Worked a charm. :-)

---

### Post by geirha on 2009-05-10
You can do that without first copying the sql file as well.
```
ssh $USER@$HOST -p $PORT "mysql -u root --password=mypass" < /home/myaccount/Sandbox/sqlupdate.sql
```

---

