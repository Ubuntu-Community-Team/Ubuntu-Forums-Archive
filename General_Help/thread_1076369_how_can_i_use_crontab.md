---
title: "how can i use crontab ?"
date: 2009-02-21
forum: General Help
---

### Post by megazayed on 2009-02-21
Hello every body

i want a help in the following task :

i have java class and i created a shell file (.sh) that run this java class and i want to run this shell file every one minute using crontab and i want to put the output in a log file named by the run time of shell file 

can any one help me in this ?

---

### Post by geirha on 2009-02-21
Open a terminal and run ```
crontab -e
``` to edit your crontab. The format of crontab is explained in [crontab(5)](http://manpages.ubuntu.com/cgi-bin/search.py?ie=UTF-8&q=crontab&titles=Title&lr=lang_en).

Assuming the shell-script is in the folder bin/ in your homedir, then the crontab entry may look like:
```
* * * * * $HOME/bin/thescript.sh > "$HOME/something-`date +%Y-%m-%d_%H:%M:%S`.log" 2>&1 
```
All output from thescript.sh will be redirected to a file called something-2009-02-21_17:18:19.log, depending on the time it is run.

---

### Post by megazayed on 2009-02-21
at first thanks for your reply 
the code did not work with me
could u tell me plz the meaning of:  2>&1 ?
and why u did not use bash command before :
$HOME/bin/thescript.sh ?
thanks

---

### Post by geirha on 2009-02-21
I assumed your script had a hashbang at the beginning (#!/bin/bash or #!/bin/sh), and had made the script executable. If you prefer to call the interpreter yourself, just do that. ```
... /bin/bash $HOME/bin/thescript.sh ...
```

```
 > filename
``` redirects stanard out to the file given by filename.
```
 2>&1
``` redirects standard error to standard out. The result of ```
>filename 2>&1
``` is that both standard out and standard error will end up in the file given by filename.

---

### Post by megazayed on 2009-02-22
really thanks for your support 
all works with me except one thing
the script is working well but i can't redirect it in a file named by the run time of the script 
do u think is there any problem in this part of code ? :
[PHP]"$HOME/something-`date +%Y-%m-%d_%H:%M:%S`.log"[/PHP]

thanks once again

---

### Post by geirha on 2009-02-22
It works fine for me
```
~$ > "$HOME/something-`date +%Y-%m-%d_%H:%M:%S`.log"
~$ ls -l something-*
-rw-r--r-- 1 geirha geirha 0 Feb 22 11:49 something-2009-02-22_11:49:47.log

```

Is the file created, but empty, or not at all?

Also, I recommend you install the [mailx](apt:mailx) package. After installing that package, cron will send you a system mail if the command it run had any output. You read such mails by running ```
mail
``` in a terminal.

---

### Post by megazayed on 2009-02-22
the file not created at all

---

### Post by geirha on 2009-02-22
Ok, just to clarify. You are running this in your user's crontab and not root's? If you run it in root's crontab (sudo crontab -e), the $HOME variable will point to /root instead of /home/*yourusername*.

---

### Post by megazayed on 2009-02-22
i have to entities in my cron tab the first
is 
```
* * * * * sh /home/ahmed/cronlog/test.sh >> /home/ahmed/cronlog/test.log

``` 
and it works well

the second:
is
```
* * * * * sh /home/ahmed/cronlog/test.sh > "/home/ahmed/cronlog/something-`date +%Y-%m-%d_%H:%M:%S`.log" 2>&1
```
and it dose not produce a timed file

---

### Post by geirha on 2009-02-22
Does cron send you any mail?

---

### Post by megazayed on 2009-02-22
No mail for root in my OS

---

### Post by geirha on 2009-02-22
How about your user?

---

### Post by megazayed on 2009-02-22
in user mail i found this error:
Syntax error: EOF in backquote substitution

---

### Post by geirha on 2009-02-22
> **megazayed said:**
> in user mail i found this error:
Syntax error: EOF in backquote substitution

Aha, that error made me have an extra look at crontab(5). The % sign has a special meaning in the crontab, which I was unaware of earlier. That means we must escape those % signs so they get interpreted by date instead of cron.

```
* * * * * sh /home/ahmed/cronlog/test.sh > "/home/ahmed/cronlog/something-`date +\%Y-\%m-\%d_\%H:\%M:\%S`.log" 2>&1
```

---

### Post by megazayed on 2009-02-22
really thanks for your support and your patience with me
the code worked well now

---

