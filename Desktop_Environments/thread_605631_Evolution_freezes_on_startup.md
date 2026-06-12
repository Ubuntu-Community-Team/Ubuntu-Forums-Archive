---
title: "Evolution freezes on startup"
date: 2007-11-07
forum: Desktop Environments
---

### Post by drlinux on 2007-11-07
I am running Ubuntu 7.06 and have been using Evolution for some time - however it has now decided to freeze on startup and does this even when I run it offline as below:

~$ evolution --offline
CalDAV Eplugin starting up ...

(evolution-2.10:6113): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:6113): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:6113): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:6113): DEBUG: mailto URL program: evolution
Killed


Can anyone advise how to correct this problem and if not how can I recover all my mail.

Thanks for any help out there

---

### Post by saphil on 2007-11-12
I can vouch for the error, and I am working on getting a debug file
```
wolf@prospero:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.10:7185): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:7185): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:7185): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:7185): DEBUG: mailto URL program: evolution

```

I am also using Feisty

---

### Post by saphil on 2007-11-12
Here is the result of a valgrind memtest.  
I haven't checked whether this is up as a bug, yet.

From the launchpad bug-tracking files.

Might be a good work-around for you
>                 [[IMG]https://bugs.launchpad.net/@@/person[/IMG] TheWalrus]("https://bugs.launchpad.net/%7Ealdousthewalrus")          wrote     on 2007-11-06:     [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/13333/comments/17")   
                     [FONT=monospace]PLAIN ENGLISH SOLUTION TO THE PROBLEM! (hopefully)
 I just had this same problem. I solved it by opening the correct mailbox then deleting the message that caused it to hang like this:
 enter the following on the command line (I used gedit, basically you need a text editor):
  ~/.evolution/mail/local/gedit <mailbox name>
 Backup the file to (for example) the desktop.
Carefully select the offending email. The email starts something like:
From <email address>...
and ends with a blank line.
 If you don't know which mail it was you may need to delete all the most recent mails until you get the correct one.
 This also means you can read the messages. Bonus!
 Hope this works for you as it did for me.
[/FONT]
        
  


---

### Post by fazavon on 2007-11-13
Well thank you for that... worked like a charm..

//j

---

### Post by saphil on 2007-11-13
It worked for me too.  I had 44 MB in my inbox.  I dumped a bunch.  Noticed I had 129MB in my sent mail.  Dumped a bunch of that too, after I had Evolution working again.

---

### Post by winderama on 2007-12-26
Can someone please help me with this.  I think my problem may be similar.  I have this problem for several months and posted a while back and received absolutely no help.  Maybe I posted in the wrong place.

[https://answers.launchpad.net/ubuntu/+question/16619](https://answers.launchpad.net/ubuntu/+question/16619)

---

