---
title: "Otrs cronjob"
date: 2009-05-01
forum: Desktop Environments
---

### Post by maximx86 on 2009-05-01
Hi,

I installed OTRS 2.3.2-2 on Ubuntu 9.04 from Synaptics, but the cronjobs (for fetching email from POP3 accounts - PostMasterMailbox.pl) are NOT installed after using the otrs2 package;

This is the example from the OTRS guide

# fetch emails every 10 minutes
*/10 * * * * $HOME/bin/PostMasterMailbox.pl >> /dev/null

The cronjob needs to be ran as 'www-data' user

It works when I do it manually:
sudo su - www-data
cd /usr/share/otrs/bin
./PostMasterMailbox.pl

Can someone help me to create the cronjob step by step? I am new to Ubuntu.

Thanks!

---

### Post by coutts99 on 2009-05-01
```
sudo crontab -e
```

Then paste your cron info in there.

```
*/10 * * * * $HOME/bin/PostMasterMailbox.pl >> /dev/null
```

Put the full path in instead of $HOME

---

### Post by maximx86 on 2009-05-01
I get permission errors as the job needs to be ran as another user: www-data. How can I do this?

I tried
*/1 * * * *  sudo su - www-data /usr/share/otrs/bin/PostMasterMailbox.pl >> /dev/null

I need to provide the password and then I get

/usr/share/otrs/bin/PostMasterMailbox.pl: 23: use: not found
/usr/share/otrs/bin/PostMasterMailbox.pl: 24: use: not found
/usr/share/otrs/bin/PostMasterMailbox.pl: 27: use: not found
/usr/share/otrs/bin/PostMasterMailbox.pl: 28: Syntax error: "(" unexpected
Press ENTER to continue and close this window.

Thank you

---

### Post by coutts99 on 2009-05-01
```
*/1 * * * * www-data /usr/share/otrs/bin/PostMasterMailbox.pl >> /dev/null
```

Will run it as www-data (I think)

---

### Post by maximx86 on 2009-05-01
Hi,

No luck I am afraid :(

I get:
line1: www-data: command not found

---

### Post by Jarod83 on 2010-02-04
This should do it:

```


# fetch emails every 10 minutes
*/10 * * * * otrs test $HOME/bin/PostMasterMailbox.pl >> /dev/null


```

---

