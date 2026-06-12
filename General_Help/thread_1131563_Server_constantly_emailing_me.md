---
title: "Server constantly emailing me"
date: 2009-04-20
forum: General Help
---

### Post by sw34963 on 2009-04-20
> Your message did not reach some or all of the intended recipients.

      Subject:	Cron <root@xxxxxx> /etc/webmin/bandwidth/rotate.pl
      Sent:	16/04/2009 1:00 PM

The following recipient(s) cannot be reached:

      [email]root@xxxxxx.syndeticom.local[/email] on 21/04/2009 1:05 PM
            Could not deliver the message in the time limit specified.  Please retry or contact your administrator.
            < xxxxxx.syndeticom.local #4.4.7 X-Unix; 71>


I am getting spammed by my server - which is somewhat funny,  I was wondering on how I would stop the process or what ever is required.

Thanks

Stuart

---

### Post by dcstar on 2009-04-21
> **sw34963 said:**
> I am getting spammed by my server - which is somewhat funny,  I was wondering on how I would stop the process or what ever is required.

Thanks

Stuart

The process sending the message is clearly listed.

---

### Post by sw34963 on 2009-04-21
> The process sending the message is clearly listed.

I assume you are talking about  "/etc/webmin/bandwidth/rotate.pl" ?

if so can you elaborate....

---

### Post by lisati on 2009-04-21
> **sw34963 said:**
> I assume you are talking about  "/etc/webmin/bandwidth/rotate.pl" ?

if so can you elaborate....

This is likely some process that is set up to automatically send out an email at set intervals (automatically doing things at set times is what 'cron' does)

---

### Post by sahabcse on 2009-04-21
paste the o/p of 

contab -e

---

### Post by sw34963 on 2009-04-21
> **sahabcse said:**
> paste the o/p of 

contab -e

I ran the command

sudo contab -e

and it came back with a 'unrecognised command' error message.
Where do you run it from?

---

### Post by sahabcse on 2009-04-21
sorry 

crontab -e

---

### Post by iponeverything on 2009-04-22
Go into webmin and turn off bandwidth monitoring:

https://<ip on your server>:10000

---

### Post by sw34963 on 2009-04-22
> crontab -e 

thanks sahabcse

Went into Webmin and turned off the bandwidth monitoring as suggested by iponeverything.  I didnt realise I had turned it on. Will see if that stops it.

Cheers Guys

---

### Post by sw34963 on 2009-04-22
So,  that didn't work.  Here is the output of 'contab -e'

```
10 14 * * * /etc/webmin/cron/tempdelete.pl

```

It doesn't look like that is connected to this problem.

This is the OP og /etc/webmin/bandwidth/rotate.pl  if it helps

```
#!/usr/bin/perl
open(CONF, "/etc/webmin/miniserv.conf");
while(<CONF>) {
        $root = $1 if (/^root=(.*)/);
        }
close(CONF);
$ENV{'WEBMIN_CONFIG'} = "/etc/webmin";
$ENV{'WEBMIN_VAR'} = "/var/webmin";
chdir("$root/bandwidth");
exec("$root/bandwidth/rotate.pl", @ARGV) || die "Failed to run $root/bandwidth/rotate.pl : $!";

```

---

### Post by sahabcse on 2009-04-23
Hi

try the following


# crontab -u root -e
change the line :
0 * * * * /etc/webmin/bandwidth/rotate.pl

into
0 * * * * /etc/webmin/bandwidth/rotate.pl >/dev/null 2>&1

---

### Post by sw34963 on 2009-04-26
> **sahabcse said:**
> Hi

try the following


# crontab -u root -e
change the line :
0 * * * * /etc/webmin/bandwidth/rotate.pl

into
0 * * * * /etc/webmin/bandwidth/rotate.pl >/dev/null 2>&1


Yeh,  I found this fix also,  but I didnt have the first line in my crontab.  Anyway I entered the second line into it  but still no joy.

Would simply just killing the rotate.pl process fix it or cause more problems?

---

### Post by sw34963 on 2009-04-26
UPDATE: Well,  it appears that it has worked,  but took sometime as I haven't recieved and email all day.  
As per the previous post,  I had made the entry into the crontab, but still recieved emails afterwoods.  Now it appears to have stopped.

Thanks for your help.

---

