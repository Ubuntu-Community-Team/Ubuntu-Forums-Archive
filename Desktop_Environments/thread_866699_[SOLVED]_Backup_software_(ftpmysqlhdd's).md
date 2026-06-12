---
title: "[SOLVED] Backup software (ftp/mysql/hdd's)"
date: 2008-07-22
forum: Desktop Environments
---

### Post by tvds on 2008-07-22
Hi I am looking for gui backup software to backup my media / photo's / music etc.

But I also like to be able to backup my websites (on outside server) and mysql dbases.

Any software out there that meets my demands ?

(using Handybackup for windows for it now)

Thanxs

---

### Post by Potatoj316 on 2008-07-22
You could just copy the files to your backup media.  Or you could throw them all in a .tar then use gzip or your favorite compression to compress them.

---

### Post by tvds on 2008-07-22
Sorry I think I was nog clear.

I am looking for automated software. So it can run every 5 days or so.

(yes cron job, but then something with a gui)

---

### Post by Potatoj316 on 2008-07-22
You want a GUI to set it up but then run every day?  I think it would just be easier to create a shell script to tar and gzip everything for you.  Have you checked the repositories? try:
```
aptitude search backup
```

---

### Post by tvds on 2008-07-22
Yes I like to create al kinds of backups.

So it is not like I do this once and than it runs for the next year.

I create lots of websites, which are changing a lot. I have multiple pc's etc etc..

So the gui is more for the easy setup of the backup jobs I create every week for different purposses.

---

### Post by hyper_ch on 2008-07-22
rsync & cron and for the mysqldbs a small script with mysqldump.

---

### Post by Potatoj316 on 2008-07-22
you could write a script that asked for input.  Have you tried that search I outlined?

Oh and hyyper_ch there are 11 types of people in the work, those who understand binary, those who dont, and those who have a shirt that says what you originally said

---

### Post by tvds on 2008-07-22
Thank you very much for all your replies.

Another question.

Did anyone really read my first question ?

Let's try it again.

I'm looking for backup software with a _GUI_ for backing up HDD stuff, ftp and mysql possibility.

Nope, don't want to write scripts.

I'm a windows user, I like things easy but working that is why I want to use ubuntu.

---

### Post by Potatoj316 on 2008-07-22
Did you try my search?  That might have found something.  

I realize you want a GUI but there might not be one.  Many linux users like to use the terminal, it gets things done fast.  I used to try to stay as far away from the terminal as possible but then I realized how useful and easy it is.

---

### Post by hyper_ch on 2008-07-22
you wouldn't even have to write the scripts as they are already out there... it's just a matter of searching them and knotting them together...

I also like things the easy way and a script does that because (1) I konw what's going on and (2) I can modify it very easily and (3) I can use it on all distros ;)

But as Potatoj has said, there might not be GUI that does all you want - so good luck on finding one.

---

### Post by swisscow on 2008-07-22
I don't know about mysql etc, but for backing up photos, music etc I use Unison (it's in Synaptic). I've set up a few profiles to back up my home folder to an external drive and music to my mp3 player. the nice thing is that after it has run for the first time, it then only looks at things that have changed. It's fairly straightforward to run, the only thing I had to do was add the line perms = 0 to the profile in the hidden unsion folder in home. (This tells it to ignore permissions).

I know this is not a true back up system (grandfather, father etc) but it is very easy to run and understandable. I haven't tried to schedule it because I use the computer on an irregular basis.

Hope this helps

---

### Post by tvds on 2008-07-22
I know many linux users like terminal sessions.

But... they might not use ubuntu. They fix their own distro.

I am a simple ubuntu user. Want it out of the box (well almost out of the box) I did a server install took me the whole week to set it up right, but it works.

Now for my client pc I just want it plain and simple. No writing of knotting up scripts.  If I wanna knott scripts I'll go and do it myself, because then I can learn something about it. But for every backup script it will take me a day. (in windows I can do, click click ready)

For now.... just the easy way, no time to go find out what to write to make a backup.

Yes Potatoj316 I searched your search. Thank you for that.
Did not get what I wanted.

I understand that there might not be a sollution for me (yet). Than I will end up writing and knotting up scripts.

Thanxs so far. :)

---

### Post by Potatoj316 on 2008-07-22
What directories do you want to backup, where do you want to back them up to and at what times/how often

---

### Post by tvds on 2008-07-22
Does that really matter ?

Any Directory
Any FTP root dir
Any MySQL dbase

:???:

Now, tomorrow, next week. Every day, every month, yearly. At 03:00 AM, 04:45 PM, 10:32 AM

---

### Post by Potatoj316 on 2008-07-22
Ok here you go, this will backup /home every day at 03:00 AM, 04:45 PM, and 10:32 AM.  First you have to create this shell script (make a text document called backup.sh and put it in /bin)
```
#!/bin/bash
# creates a backup of /home called backup.tar
# put in /bin

tar cf backup.tar /home
```

To get it to run every day you have to edit the crontab.  To edit the crontab type (in a terminal)
```
crontab -e
00 03 * * * /bin/backup.sh
45 16 * * * /bin/backup.sh
32 10 * * * /bin/backup.sh
```

when you type the first line you should get a text editor, put the following lines in the text editor, save the document, and close the editor.

---

### Post by tvds on 2008-07-22
Thank you.

Problem solved ! 

I just closed this subject.

---

