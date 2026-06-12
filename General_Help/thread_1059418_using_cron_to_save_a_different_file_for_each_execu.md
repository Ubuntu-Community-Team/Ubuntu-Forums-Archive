---
title: "using cron to save a different file for each execution"
date: 2009-02-03
forum: General Help
---

### Post by oalexandrino on 2009-02-03
hello all,

i have a cron's job that executes twice a day.

for each execution it saves the shell script's output in a file.

the problem is for all executions the content for the previous one is replaced by the last one.

i'd like to save a new file (where the file's name would be based in the current time) for each execution.

my cron's job follows this pattern:
```

0 1 * * * /home/guest/scripts/do_backup.sh > /home/guest/logs/do_backup.log
```

how can i implement this?
is it possible?

---

### Post by sisco311 on 2009-02-03
```
command > file-name-`date +%F-%H:%M:%S`
```
```
man date
```

or put the date command in your script and append the log file:
> #!/bin/sh
date +%H:%M
...

```
command >> file-name
```

---

### Post by whitegourd on 2009-02-03
I may be wrong about this (anyone, please jump in if I am ...), but if I'm not mistaken, you'd want to add the path into your environment.

I usually keep my scripts in /home/user/bin ... or /usr/local/bin.

---

### Post by oalexandrino on 2009-02-04
I've got an error

```
/bin/sh: Syntax error: Unterminated quoted string
```

the command would be like this...how to add what u have said?

```
0 12 1,2,3,4,5 * * root  /home/guest/scripts/cidades1_http_bkp.sh  > /home/guest/scripts/logs/saida_http_bkp.txt
```

about the script's location ibt is just an example, but btw..what's the pattern to put scripts?

> **sisco311 said:**
> ```
command > file-name-`date +%F-%H:%M:%S`
```
```
man date
```

or put the date command in your script and append the log file:

```
command >> file-name
```

---

### Post by whitegourd on 2009-02-04
0 12 1,2,3,4,5 * * /home/guest/scripts/cidades1_http_bkp.sh  > /home/guest/scripts/logs/saida_http_bkp.txt

See if taking the user out of the equation will do it.

0 12 1,2,3,4,5 * * /home/guest/bin/cidades1_http_bkp.sh  > /home/guest/scripts/logs/saida_http_bkp.txt

I'd suggest keeping the scripts in the bin directory if you can, create one if there isn't one already and then add it to your $PATH.  To see what you currently have set in your path ...

echo $PATH

I don't have any experience in creating a cron based on a users' log in.  I've always used root to run all my cron jobs and keep the scripts in /usr/local/bin.  There are probably easier ways of doing this, but for me, this has worked for years w/o any problems.

---

