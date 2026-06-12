---
title: "Evolution inbox problem"
date: 2009-04-09
forum: General Help
---

### Post by captainron042 on 2009-04-09
I searched for a fix to this problem, but I have not found a solution. Maybe it just looked in the wrong places?, so I'm sorry if this is a reposted problem and there is a fix.

Out of the blue, when I opened my evolution, I see nothing in the inbox.
the subfolders still have their e-mails in them, but I see none of the emails that I had in my inbox or any new emails. 

When I start Evolution up, I see a message at the bottom that says 
  Error while opening folder mbox:/home/myname/.evolution/mail/local #inbox

I exited and restarted evolution, restarted the computer. nothing.
I even took advice from one thread and moved all the files in ../local to a temp folder, then restarted evolution, then closed evolution, moved them back, and restarted evolution. this didn't fix it.

Please help. I have a college assignment due monday, and need an e-mail that was in my inbox!

---

### Post by dcstar on 2009-04-09
> **captainron042 said:**
> I searched for a fix to this problem, but I have not found a solution. Maybe it just looked in the wrong places?, so I'm sorry if this is a reposted problem and there is a fix.

Out of the blue, when I opened my evolution, I see nothing in the inbox.
the subfolders still have their e-mails in them, but I see none of the emails that I had in my inbox or any new emails. 

When I start Evolution up, I see a message at the bottom that says 
  Error while opening folder mbox:/home/myname/.evolution/mail/local #inbox

I exited and restarted evolution, restarted the computer. nothing.
I even took advice from one thread and moved all the files in ../local to a temp folder, then restarted evolution, then closed evolution, moved them back, and restarted evolution. this didn't fix it.

Please help. I have a college assignment due monday, and need an e-mail that was in my inbox!

First make sure you do not have a search filter set, then go into the .evolution local directory and delete/move and .summary, meta and index files (do not delete the actual mail files - these are the larged sized ones).

Then restart Evolution and see if things are better.

---

### Post by captainron042 on 2009-04-09
I tried that several times after your suggestion, even shutting down between steps. All to no avail. 

I moved the large inbox file and evolution made a new one. I had no problems, then, getting new e-mails.

I shut it down again, and replaced the inbox file with its original, and got the same problems again. It seems like that file is corrupted or something? is there any way I can test that theory or, more importantly, fix it?

---

### Post by dcstar on 2009-04-11
> **captainron042 said:**
> I tried that several times after your suggestion, even shutting down between steps. All to no avail. 

I moved the large inbox file and evolution made a new one. I had no problems, then, getting new e-mails.

I shut it down again, and replaced the inbox file with its original, and got the same problems again. It seems like that file is corrupted or something? is there any way I can test that theory or, more importantly, fix it?

Is it really large, like over 2GB? (I think that there is a 2GB limit).

Actually, you might want to use the Evolution Backup function, close Evolution, rename the whole .evolution folder, restart Evolution and then do a restore from the file you just backed up.

---

### Post by captainron042 on 2009-04-11
Good idea. Thanks for your help.
 I tried it, but it didn't work :(

---

### Post by Zill on 2009-04-11
These links may help...
[URL="https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/233993"]
https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/233993[/URL]

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/197290]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/197290")

In particular, make sure your Trash is emptied regularly and consider archiving old emails as suggested by nocturrne in [this post]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/197290/comments/18").

---

### Post by captainron042 on 2009-04-20
Thanks for those links. Looks like the problem has been around awhile. 

I am trying Nocturne's solution, but I'm running into an issue. Here's his post

*****
I have the same problem every 6 months or so. This lame bug has been around since at least 2005. Please fix it.
Ubuntu Gutsy 7.10
Evolution 2.12.1
The best workaround I have found is to use archivemail to archive the old mail in the file, reducing the file size.

install archivemail:
sudo apt-get install archivemail

archive all mail older than 90 days:
archivemail -d90 ~/.evolution/mail/local/yourmailfile

After doing this, the file size is reduced way below 2GB, so it will open the next time you start evolution. If you like you can decompress the archive file and import it into another folder in evolution - takes a while though...
*****

So I installed archivemail. At the next step, I'm typing in this...

archivemail -d90 ~/.evolution/mail/local/inbox
and getting this...
No such file or directory

I tried it without the "-d90" and that didn't work, either. I know I recently got a large pdf file sent to me when this problem occured, and I didn't have many email in my inbox. It's probably mostly that one e-mail that screwing it all up, and it was more recent than 90 days. I tried "-d02", but that didn't work

---

### Post by Zill on 2009-04-21
> **captainron042 said:**
> 
So I installed archivemail. At the next step, I'm typing in this...

archivemail -d90 ~/.evolution/mail/local/inbox
and getting this...
No such file or directory...

I believe *inbox* should be *Inbox* (linux is case-sensitive).

You can confirm this by listing the directory with the command...
```
ls ~/.evolution/mail/local/
```

If so then give the following a try...
```
archivemail -d90 ~/.evolution/mail/local/Inbox
```

---

### Post by captainron042 on 2009-04-21
That did it! Thanks!

---

