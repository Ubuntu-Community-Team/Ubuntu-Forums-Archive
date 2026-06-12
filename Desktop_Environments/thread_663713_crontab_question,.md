---
title: "crontab question,"
date: 2008-01-10
forum: Desktop Environments
---

### Post by lithiumKid1976 on 2008-01-10
hi,
im new to cron , and was looking for some help.

i have edited my crontab file 

basically i want it to run the updatedb command, and then redirect it to a txt file. here what i use. 

* * * * * /usr/bin/updatedb -v > updatedb.txt

(i think its due to run every minute, just something im messing with to see will it run, i know its not an ideal comman, or even that usefull :))


but it does not seem to work.

so what im wondering if its possible to do such a thing. ie schedule a command, using cron and have it run in a terminal.??


any help appreaciated.
Damien

---

### Post by hal8000 on 2008-01-10
Your command as typed will send the output of updatedb to a file in the same directory, i.e. /usr/bin

If you wanted the output to go to your home directory you would use

updatedb -v /home/username/updatedb.txt  (Replace username with your user name)

If that doesnt work it may be because the command needs quoting :
"updatedb -v /home/username/updatedb.txt"

Using * * * * * will run the command every minute, as updatdb can take while you may have multiple
processes running.

I never bother with updatedb just use the find command when I need to.

---

### Post by lithiumKid1976 on 2008-01-11
Thanks for your reply. i have it working now.
i mainly going to use it to keep an eye on disk space, and ping certain sites etc.

any other suggestions for what you can get your crontab to do, that would be handy?

Thanks
damien

---

### Post by hal8000 on 2008-01-13
You can schedule a crontab to do almost anything. If you can start it from a terminal then its possible.

I dont use a crontab now, but when I did I just set it to filter spam from my emails accounts by calling popsneaker. Popsneaker is a command line tool for deleting spam; the advantage is that it can delete spam without you having to pull it off a mails erver and wasting bandwidth.

---

