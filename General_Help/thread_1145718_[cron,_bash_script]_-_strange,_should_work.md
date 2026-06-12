---
title: "[cron, bash script] - strange, should work?"
date: 2009-05-01
forum: General Help
---

### Post by whorush on 2009-05-01
i'm running 9.04 on amd64.  check out this stupid script..

```
#!/bin/bash
touch /home/pd/Desktop/1
```

when i run this script as either root or my user at the prompt it makes the file.  when cron runs it, it doesn't.  wtf?!?!

btw, i'm using some cute gnome scheduled tasks front end to cron?  does that matter?

thanks!

(btw, how do i get cron to send me emails when my job runs?  i have an MTA set up already, ssmtp.   the other MTA's i think are super hard to set up.  i've tried somet things they don't work?)

---

### Post by Kareeser on 2009-05-01
cron _should_ run under your own user account... I'll let someone else handle that.

In any case, cron also sends you emails using local mail. You won't need an MTA for that. It just gets dumped to /var/mail/yourusername

---

### Post by whorush on 2009-05-02
thanks for trying.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
this says that in order for a user to run something they should be in /etc/cron.allow.  which didnt exist.  so i made it and added my username as it says here... [http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/ch-autotasks.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/ch-autotasks.html)  because the ubuntu guide didn't say how to edit it.

i also checked my /var/mail/ folder and it was completely empty.  how do i set that up?  i want it to actually email me the output, so i can act on it.  so for that i guess i need an MTA?  which luckily i have :-) but how do i connect them?

pretty lost, thanks!

---

### Post by joeabiraad on 2009-05-02
Hey

open a terminal and write (make sure you are logged in using the desired username... i think it should be pd)

```
crontab -e
```

Here you should see a list of all the cronjobs you created under this username.
It should look something like this

```
5 * * * * ( /bin/ps -ax | /usr/bin/grep -v grep | /usr/bin/grep -q /usr/local/ap
ache2/bin/httpd ) || ( /www/bin/apachectl restart)
```

Now at the beginning of the file add 

```
MAILTO=bleh@blah.com
```

save and exit.

You should receive now an email every time your script is executed :)

Hope it helps
Jo

---

### Post by dcstar on 2009-05-02
> **whorush said:**
> i'm running 9.04 on amd64.  check out this stupid script..

#!/bin/bash
touch /home/pd/Desktop/1

when i run this script as either root or my user at the prompt it makes the file.  when cron runs it, it doesn't.  wtf?!?!
.........

Probably because **you** are assuming cron runs in the same environment as a user shell - it doesn't.

You should prefix all commands with the full path in the cron entry (as well as inside the script), eg: /home/whatever/path-to-script

---

### Post by whorush on 2009-05-02
thanks everyone!  i'm done!

i was trying all this stuff, but it never worked somehow.  now it does :-).  i must have been messing up little things.

for instance, last night i was tired and i made a dumb mistake.  i was setting that cron job to run a minute later, over and over again, and watching it, and it was 10pm, so i put in 10 for the hour field instead of 20!!!  so thats why it wasn't running!

but still, for sure, there was a line in my real script that i didn't want to trouble you all with that wasn't working at all...
```
echo "Subject: test" | ssmtp me@gmail.com
```

but david figured that one out, its ...
```
echo "Subject: test" | /usr/sbin/ssmtp me@gmail.com
```

and its clear, because when i looked at the output of the script with that first ssmtp line in it, the output says it couldn't find ssmtp.

Also, i had tried that MAILTO and it didnt work, this time it did?  it is using ssmtp to send it.   don't know how it found it, but it did.  i guess somewhere ssmtp told ubuntu i'm going to handle emails?

thanks again!

---

### Post by whorush on 2009-05-02
ok, ok, one last little thing :-)

at the end of my real script, i run...

```
sudo ifconfig eth0 down
```

to turn the network off after it downloads the file, for security reasons.

problem is, that the network is off, so cron can't email the output.  it doesn't email the output when i turn the network back on either.  i wonder if its saving the email somewhere?  maybe /var/mail/yourusername ???  but its empty.  besides, if it was saving it in some kind of queue, then wouldn't it send it when i get back online?

i also don't think its saving a log either?  at least i can't find it.

is there a way to get it to save a log?  and to get it to email me as soon as i get back online?  or even better, right after my script runs?

thanks again!

---

### Post by whorush on 2009-05-02
btw, why couldnt cron find ssmtp.  its not running as a different user?  just in a different environment?

so different environment means different path variables and what not, right?

am i on the right track?

thanks!

---

### Post by whorush on 2009-05-02
actually, just by accident, i found it in dead.letter in my home directory?

---

