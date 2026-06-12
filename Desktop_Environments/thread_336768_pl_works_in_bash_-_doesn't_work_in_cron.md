---
title: "pl works in bash - doesn't work in cron"
date: 2007-01-12
forum: Desktop Environments
---

### Post by John_a12357 on 2007-01-12
I have a script that works good when executed under bash, but will not execute from cron. I have spent 5 hours trying to figure out and have given up. I am sure it is some environmental variable that I have not set but am unable to figure out which one.

cron setting:
25 14 * * 1,2,3,4,5  /home/john/DS/camp_update.pl

I have added this to .bashrc so the script will execute from any folder:
export PERL_HOME='/usr/bin/perl'
PATH=.:$PERL_HOME:$PATH

the .bash_profile in my home dir. has this in it:
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi
if [ -d ~/bin:"$PATH}"
fi
# I added this thinking it would help - it didn't
PATH=$PATH:/home/john/DS

I have also started KCron and tried to execute the program using "Run Now" - no good.

I have Ubuntu lamp server, with Kubuntu installed on top of it - if this helps.

Any help would be most appreciated, and thank you in advance.

---

### Post by Arndt on 2007-01-12
> **John_a12357 said:**
> I have a script that works good when executed under bash, but will not execute from cron. I have spent 5 hours trying to figure out and have given up. I am sure it is some environmental variable that I have not set but am unable to figure out which one.

cron setting:
25 14 * * 1,2,3,4,5  /home/john/DS/camp_update.pl

I have added this to .bashrc so the script will execute from any folder:
export PERL_HOME='/usr/bin/perl'
PATH=.:$PERL_HOME:$PATH

the .bash_profile in my home dir. has this in it:
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi
if [ -d ~/bin:"$PATH}"
fi
# I added this thinking it would help - it didn't
PATH=$PATH:/home/john/DS

I have also started KCron and tried to execute the program using "Run Now" - no good.

I have Ubuntu lamp server, with Kubuntu installed on top of it - if this helps.

Any help would be most appreciated, and thank you in advance.

Is there no output at all from the cron run? It's supposed to mail you any output.

---

### Post by mannheim on 2007-01-12
Nothing you put in your .bashrc or .bash_profile files will have any relevance for the cron jobs, I believe.

For users' cron jobs, $PATH is always just "/usr/bin:/bin" and .bashrc and .bash_profile are not sourced.

---

### Post by John_a12357 on 2007-01-12
no there is nothing, to get an e-mail isn't there a setting I must make to tell cron to send me an e-mail?

---

### Post by mvaniersel on 2007-01-12
You can divert the output of the script directly to a log file, so you won't have to bother with setting up email.

For example:

25 14 * * 1,2,3,4,5 /home/john/DS/camp_update.pl >> /home/john/log.txt 2>&1

this will append both stdout and stderr to log.txt after every run.

---

