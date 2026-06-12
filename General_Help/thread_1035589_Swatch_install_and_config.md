---
title: "Swatch install and config"
date: 2009-01-09
forum: General Help
---

### Post by lucloubier on 2009-01-09
Hello everyone !

I have install Swatch (apt-get install swatch) on my 8.04 server.

I have done some googling to seach for configuration tips, but I have not found any useful link.

Does anyone can help me to configure it properly ?
where is the config file? 
Is there any documentation available on this?

Thanks in advanced

---

### Post by lucloubier on 2009-01-17
Noone seems to be using it ?

---

### Post by lucloubier on 2009-03-10
For those of you interested in using swatch, here is what I have found (so far) googling the net for info and then applying it afterwards to my own ubuntu 8.04 LTS home server! 

I googled the web for a detailed howto... but I found nothing  easely usable by any linux newbie ! This is one reason I wrote this so people like me will get some quick help on this.

I keep my server uptodate with ubuntu released patches by running "**apt-get upgrade**" on a weekly (regular) basis ! 

I also need to mention I run postfix (swatch uses mail to warn when it finds what you asked him to monitor!).

Here is what I did :
[LIST=1]
[*]Install swatch using "**apt-get install swatch**" console command
[*]created a file (** /etc/swatch.conf **in my case) to tell what string to monitor and whom to warn upon detection
[*]manually launch swatch to monitor a specific log and send me an email if that event occurs : root@loubier:~# **/usr/bin/swatch -c /etc/swatch.conf -t /var/log/syslog &** and hit twice ENTER
[*]manually kill swatch when log rotates 
root@loubier:~# **ps -ef | grep swatch*** to get the process number ID
root@loubier:~# kill (and looking for a way to automate it - suggestions are welcome !)
[*]still trying to make it run as a service (any suggestion on how to do so ?)!
[/LIST]

More to come... as soon as I find it!

---

### Post by jchung on 2009-04-15
Came across this thread as I was googling for swatch and ubuntu.

Regarding how to run swatch as a service... The typical way is to create a script in /etc/init.d that will run swatch as you want it to. Then create a soft link in /etc/rc2.d that points back to the script in /etc/init.d

I would guess you'd want swatch to start right after syslog starts. So probably want to give the link in rc2.d a name like S11swatch. On my system, the syslog is S10sysklogd so setting swatch to S11 will ensure it runs shortly after syslog does.


Joo

---

### Post by lucloubier on 2009-04-15
Hi jchung !

Would you mind posting that script (your own or an example)so I can give it a try ?
 
Thanks !

---

### Post by postal88 on 2010-03-03
Since I had to piece this together from many sites, I'm adding this here in the interest of completeness:

If you need a more robust tool for and intrusion detection system (IDS), **snort** bundles swatch with other tools to provide a more comprehensive solution. I'm using swatch to monitor non-system application logs.  Otherwise, you're probably reinventing the wheel.

**The swatch command:**
```
swatch --config-file=swatch-auth.conf --tail-file=/var/log/auth.log --tail-args=--follow=name --daemon
```
[LIST]
[*]**swatch** -- by itself uses the hidden *~.swatchrc* file as its config file and the */var/logs/syslog* as the tail file to watch.
[*]**--config-file=<filename> **-- tells swatch to use a different config file.
[*]**--tail-file=<filename>** -- tells swatch to use a different tail file (the log to watch).
[*]**--tail-args=--follow=name** -- tells the *tail* program to use the *--follow=name* argument instead of the *-f* argument.  This keeps *tail* from "stopping" when the log rotates because *tail --follow=name* follows the *filename*, _not_ the *node id* as *tail -f* does.  Tail *looks* like it stopped because you're still tailing the old rolled off log file.  This precludes the need to stop and start swatch for log rolling.
[*]**--daemon** -- tell swatch to run the process in the background so you don't have to leave it open in an authenticated terminal.
[/LIST]
**A sample config entry** to send an email (using postfix's sendmail interface) and a text message (ATT -- look up your carrier) when someone tries to su to root:

  ```
watchfor /FAILED su for root/
        exec echo "Subject: auth: FAILED su for root\n\n$_\n" | sendmail "sysadmin@mydomain.org;5555555555@txt.att.net"
```
[LIST]
[*]**FAILED su for root** -- the regular expression to trigger on
[*]**exec** -- executes an external command without stopping swatch to do it.  In this case an echoed email piped into sendmail.
[*]**Subject: auth: FAILED su for root** -- the email subject as postfix/sendmail expects it.  You could add From, To, etc to make it more robust.
[*]**\n** -- line feeds. I hope those are self-explanatory.
[*]**$_** -- prints the flagged log line, ***not*** *$0* or *$** as the man page states!
[/LIST]

---

