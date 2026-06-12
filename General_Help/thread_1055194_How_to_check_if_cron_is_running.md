---
title: "How to check if cron is running?"
date: 2009-01-30
forum: General Help
---

### Post by oalexandrino on 2009-01-30
Hello everybody,

i have the same problem described in the following post:

[http://ubuntuforums.org/showthread.php?t=126576](http://ubuntuforums.org/showthread.php?t=126576)

the problem i am unable to check what's the problem.

i have set the cron job right...but i see nothing, that is, it doesn't work.

how can i redirect the command's output to a file, for instance?

in time that i set the command up, i was logged as a user that had privileges but i really don't know what to check if it's up.

how to set up cron to send an email?

PS: i created this new thread because i had no rights to add a reply in the one above

---

### Post by Barriehie on 2009-01-30
> **oalexandrino said:**
> Hello everybody,

i have the same problem described in the following post:

[http://ubuntuforums.org/showthread.php?t=126576](http://ubuntuforums.org/showthread.php?t=126576)

the problem i am unable to check what's the problem.

i have set the cron job right...but i see nothing, that is, it doesn't work.

how can i redirect the command's output to a file, for instance?

in time that i set the command up, i was logged as a user that had privileges but i really don't know what to check if it's up.

how to set up cron to send an email?

PS: i created this new thread because i had no rights to add a reply in the one above

Can't help with all of that but you can redirect output like this:

[php]command/somefile.sh 1>path-to-logfile 2>path-to-logfile[/php]1 represents stdout and 2 represents stderr.  If you want stderr to be appended to the logfile then 2>>path to logfile.

Barrie

---

### Post by oalexandrino on 2009-02-03
Hi, thanks for replying.

So, i've solved this problem.

I had to create, by hands, a file (with the same name of the user who would run the command) in the following directory


[PHP] /etc/cron.d[/PHP]

just after i have saved the filed, the job worked fine.

but when I had used the following command

[PHP] crontab -e[/PHP]

nothing happened.

:)


thanks!

> **Barriehie said:**
> Can't help with all of that but you can redirect output like this:

[php]command/somefile.sh 1>path-to-logfile 2>path-to-logfile[/php]1 represents stdout and 2 represents stderr.  If you want stderr to be appended to the logfile then 2>>path to logfile.

Barrie

---

### Post by whitegourd on 2009-02-03
could the problem be the script/program that you're running?  I had an issue before where I wanted to run one of my scripts in the cron, but it wouldn't work.  Found out that I had to make an adjustment in my script.

run a quick test to see if that's the case ...

# test cron daily at 1am
0 1 * * * echo "test" > /tmp/test.txt

If the file is there in /tmp, then I suspect that the script could be the problem.

For emailing something to yourself from the cron ...

# test cron daily at 1am and email to da man ...
0 1 * * * echo "test" > /tmp/test.txt | mail -s "test email subject line" [email]username@domain.com[/email]

---

### Post by oalexandrino on 2009-02-03
no, it wasn't.

I had tried a simple one like u said but it didn't work.

when it didn't work i had done these steps

1) log as user who would have a cron job
2) crontab -e
3) edit the current user's crontab
4) save
5) crontab -l => yes, it is showed

but, nothing worked

i created a file in "cron.d" folder and then it worked fine.

I don't know why the first step, didn't

i could do what I wanted, if you know why i was unable to do by following the first steps i'd be glad (im curious)

many thanks!



> **whitegourd said:**
> could the problem be the script/program that you're running?  I had an issue before where I wanted to run one of my scripts in the cron, but it wouldn't work.  Found out that I had to make an adjustment in my script.

run a quick test to see if that's the case ...

# test cron daily at 1am
0 1 * * * echo "test" > /tmp/test.txt

If the file is there in /tmp, then I suspect that the script could be the problem.

For emailing something to yourself from the cron ...

# test cron daily at 1am and email to da man ...
0 1 * * * echo "test" > /tmp/test.txt | mail -s "test email subject line" [email]username@domain.com[/email]

---

### Post by whitegourd on 2009-02-03
All the cron jobs that I run are run as root.  When you modify the crontab ... do you type this in the terminal?

sudo crontab -e

also see if you have cron running ...

ps -ef | grep cron

---

