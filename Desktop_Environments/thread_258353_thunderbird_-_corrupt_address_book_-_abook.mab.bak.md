---
title: "thunderbird - corrupt address book - abook.mab.bak"
date: 2006-09-15
forum: Desktop Environments
---

### Post by krus on 2006-09-15
For the past few weeks, the strangest thing has been happening with my (generally well behaved) thunderbird client.  Anytime I launch the program, (slightly less often than daily), I'm told that my history file can't be opened.  It's backed up as history.mab.bak (then history.mab-1.bak, history.mab-2.bak, etc.) It's happened a few times with impab.mab. Those files being wiped clean didn't bother me, so when I couldn't find other people posting about the same symptoms, I put off solving the problem.  Today, however, my personal address book got corrupted too. Unacceptable.  I regularly backup, so nothing should be lost forever... but I need your help putting a stop to this craziness.

Some details:

thunderbird 1.5.0.5(20060728 )
kubuntu 6.06  
2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686

ls -lt of my thunderbird profile folder is below.

Thanks in advance for any insight.

```
karen@s2:33nhiij4.slt$ ls -lt .
total 8824
-rw-r--r--  1 karen users   41059 2006-09-15 16:24 panacea.dat
-rw-r--r--  1 karen users 3479408 2006-09-15 16:24 XUL.mfasl
-rwxr-xr-x  1 karen users   43586 2006-09-15 16:24 localstore.rdf
-rw-r--r--  1 karen users    2512 2006-09-15 13:24 history.mab
-rwxr-xr-x  1 karen users  682269 2006-09-15 13:16 downloads.rdf
drwxr-xr-x 11 karen users    4096 2006-09-15 10:43 extensions
-rw-r--r--  1 karen users    1415 2006-09-15 10:07 abook.mab
lrwxrwxrwx  1 karen users      15 2006-09-15 10:03 lock -> 127.0.0.1:+8532
-rwxr-xr-x  1 karen users   65536 2006-09-14 20:46 cert8.db
-rwxr-xr-x  1 karen users   16384 2006-09-14 20:46 key3.db
-rwxr-xr-x  1 karen users   52876 2006-09-14 20:46 prefs.js
-rwxr-xr-x  1 karen users    3027 2006-09-14 20:46 virtualFolders.dat
drwxr-xr-x  4 karen users    4096 2006-09-14 12:57 ImapMail
-rwxr-xr-x  1 karen users  127909 2006-09-14 11:34 abook.mab.bak
-rw-r--r--  1 karen users   36624 2006-09-14 10:18 history.mab-11.bak
-rw-r--r--  1 karen users    1415 2006-09-14 09:33 impab.mab
-rwxr-xr-x  1 karen users  949597 2006-09-13 18:21 training.dat
-rw-r--r--  1 karen users   26385 2006-09-13 12:36 impab.mab-5.bak
-rw-r--r--  1 karen users   26385 2006-09-12 11:29 impab.mab-4.bak
-rw-r--r--  1 karen users   31784 2006-09-11 13:31 history.mab-10.bak
-rw-r--r--  1 karen users  144088 2006-09-08 15:17 compreg.dat
-rw-r--r--  1 karen users    1274 2006-09-08 15:17 extensions.cache
-rw-r--r--  1 karen users    1300 2006-09-08 15:17 extensions.ini
-rw-r--r--  1 karen users   14379 2006-09-08 15:17 extensions.rdf
-rw-r--r--  1 karen users  101261 2006-09-08 15:17 xpti.dat
-rw-r--r--  1 karen users   12884 2006-09-08 15:04 install.log
-rw-r--r--  1 karen users    2448 2006-09-08 10:46 impab.mab-3.bak
-rw-r--r--  1 karen users   30128 2006-09-07 16:55 history.mab-9.bak
-rw-r--r--  1 karen users    3374 2006-09-07 12:11 impab.mab-2.bak
-rw-r--r--  1 karen users   26942 2006-09-07 10:06 history.mab-8.bak
-rw-r--r--  1 karen users   34978 2006-09-06 11:41 history.mab-7.bak
-rwxr-xr-x  1 karen users    8328 2006-09-01 10:44 mimeTypes.rdf
-rw-r--r--  1 karen users   28819 2006-08-30 10:36 history.mab-6.bak
-rw-r--r--  1 karen users   33395 2006-08-29 15:13 history.mab-5.bak
-rw-r--r--  1 karen users    2633 2006-08-28 14:49 impab.mab-1.bak
-rw-r--r--  1 karen users   27796 2006-08-28 11:53 history.mab-4.bak
-rw-r--r--  1 karen users   37389 2006-08-25 10:12 history.mab-3.bak
-rwxr-xr-x  1 karen users     438 2006-08-25 09:36 3076152.s
-rw-r--r--  1 karen users   27373 2006-08-24 09:22 history.mab-2.bak
-rw-r--r--  1 karen users    7385 2006-08-23 12:10 history.mab-1.bak
-rwxr-xr-x  1 karen users  479690 2006-08-20 17:25 history.mab.bak
-rwxr-xr-x  1 karen users   57457 2006-08-16 17:27 impab.mab.bak
-rwxr-xr-x  1 karen users     311 2006-08-16 17:18 cookies.txt
drwxr-xr-x  3 karen users    4096 2006-08-16 12:51 chrome
drwxr-xr-x  7 karen users    4096 2006-08-16 12:46 Mail
-rwxr-xr-x  1 karen users    3672 2006-08-12 19:05 persdict.dat
-rwxr-xr-x  1 karen users     136 2006-08-03 09:26 compatibility.ini
-rw-------  1 karen users    1196 2006-05-26 11:41 mailViews.dat
-rwxr-xr-x  1 karen users   16384 2006-04-04 12:42 secmod.db
-rwxr-xr-x  1 karen users      24 2006-04-04 11:19 components.ini
-rwxr-xr-x  1 karen users      24 2006-03-13 11:58 defaults.ini
-rw-r--r--  1 karen users     678 2005-09-30 14:49 user.js
-rwxr-xr-x  1 karen users   13682 2005-09-30 14:42 prefs.js~
-rw-r--r--  1 karen users     679 2005-09-30 14:27 user.js~
-rwxr-xr-x  1 karen users   33514 2005-09-07 12:40 #localstore.rdf#
-rwxr-xr-x  1 karen users 2100810 2005-09-07 11:12 XUL.mfl
-rwxr-xr-x  1 karen users   11088 2005-09-07 11:12 prefs.bak
-rwxr-xr-x  1 karen users      85 2005-09-07 11:07 82099029.s
```

---

### Post by treris on 2006-09-18
I've been having the same problem with my address book for a while now, but I can't say that I've found a solution yet, either here at the ubuntuforums or at mozillazine's forums. I don't get what's going wrong all the time but it is hugely annoying. The problem arose for me about the same time I updated from Breezy to Dapper (so for quite some time now). Could it have something to do with the Ubuntu thunderbird package??

any help would be greatly appreciated

---

### Post by Galactix on 2006-09-21
As of a few weeks I suffer the same problem; the abook.mab file becomes completely garbled from a certain point.

The corruption appears to happen after the entry separator '@$${ <x> {@' (judging from a few of my corrupted abook.mab files) so I figure there is nothing wrong with my fs, it is just thunderbird not correctly opening and closing the file or treating its content, could this be?

---

### Post by Galactix on 2006-09-26
This morning an upgrade for the mozilla-thunderbird package was released through apt, hopefully it has been fixed now.

---

### Post by Galactix on 2006-09-26
Hmm... after some compatibility checks I open my Address Book, and again the file is corrupted and a new one is created. Hoping this is the last time (thunderbird will do it right this time...) I check the new abook.mab (with one new address) with a previous one; there is no change in markup. Lets see how this goes; other people still having the same problem?

By the way, we're at version 1.5.0.7 (20060922) now.

---

### Post by krus on 2006-09-28
Thanks for posting, guys.  It's encouraging that I'm not all alone with this problem.  I'm trying an upgrade to 1.5.0.7 now, and hopefully that will either fix the problem or make it easier to diagnose.

---

### Post by krus on 2006-09-28
updating to 1.5.0.7 didnt' help me either. (no surprise there...)

In the interest of finding some common thread, do other people with this problem connect to a microsoft exchange server? (Galactix? Treris? Anyone else?) One of my identities is using the exchange server (via IMAP) and the others are plain old POP.  This corruption craziness started long after I hooked up to the exchange server, but it's all I can think of as a potential difference between my Thunderbird/Dapper configuration and all the Thunderbird/Dapper configurations that are working perfectly for other people.


This problem sucks.

---

### Post by Galactix on 2006-09-29
My university recently switched from POP to MS Exchange (IMAP), I can't see how this could cause local address book corruption but it does seem a coincidence...

Since upgrade to 1.5.0.7 I have not seen the problem, lets hope it is solved (keeps fingers crossed...)

---

### Post by Galactix on 2006-10-02
I have been carefully using the addressbook the past few days, and with every day my confidence grew, I think the address book corruption has been resolved! Anyone who has other experiences?

Galactix salutes Thunderbird developers

---

### Post by tinamama on 2006-10-30
this happened to me too and it happened twice in a few months...so don't get too comfy with that address book. it happened again to me.

any solutions found? i am at a loss.

---

### Post by madmaxx on 2006-12-13
Hi
Sorry to disappoint you guys, but I am on Edgy/TB 1.5.0.8 and my abook got corrupted just yesterday while playing back a backup. Just for the sake of contributing more information that is what happened:

(I wanted to replay the laptop backups to my desktop because my laptop died.)

1. set up a second user account of my desktop (edgy).
2. started TB for the first time just to generate config files.
3. delete all new and empty config files and replace them by my own ones.
  -->  /home/../.mozilla-thunderbird/*
4. restart thunderbird
5. It did not restart even!

Then I started to manually look at single config files (inc. mail foders)
with gedit and moved them one by one, everytime restarting TB to see what is happening. At one point it finally started and showed all my emails (although it seems a few are corrupted) but when I opened the abook the first time it brought an "read/write error" and generated a new abook file.

I am not 100% sure whether my laptop had already Edgy on it as well but anyway, even from Dapper to Edgy (and according Delta in Thunderbird) that should work out fine. At least it did always in the past.

This is really very annoying because how am I going to extract all address information out of my old and unreadable abook file? I'd be very happy if someone could give me any pointers! (Please do not say XML transformation :( )

Thanks,
madmaxx

---

### Post by tinamama on 2006-12-13
well i don't have any answers...i got sick and tired of it continually happening and even consulted with the developers and never got an answer how to fix this problem. plus i've had other issues with TB as well, including other error messages and the worst yet, that it kept tagging random chat transcripts (i run a chat site and i upload the transcripts of the important chats i run) as spam and deleting them and i didn't catch it in time. after losing 2 important transcripts that i can never get back, and still not having an address book because i was afraid to rebuild just to lose again, i finally gave up and went back to outlook express. i'm not entirely happy with it because it doesn't have the spam filter, so i have to get an outside one eventually, and i got real used to being able to mark emails as "important" with TB, but it was pretty minor compared to the nuisance of all the problems i was having, so that's that. 

far too many issues with TB, so i give up.

tina

---

### Post by madmaxx on 2006-12-14
> **tinamama said:**
> well i don't have any answers...i got sick and tired of it continually happening and even consulted with the developers and never got an answer how to fix this problem. plus i've had other issues with TB as well, (...) went back to outlook express. i'm not entirely happy with it (...) far too many issues with TB, so i give up.

Ouch, moving back to OE is really a step back. ](*,) 
I fully understand your feelings about TB, I also liked it better a year ago than today and I am also thinking about an alternative. Luckily there are others than OE.
Am I right to infer that your are on Windows as you consider OE? I just checked and found that 'sylpheed' is also running on Windows. You may want to have a look at it before making the decision to switch because it has a good reputation from what I know: [http://en.wikipedia.org/wiki/Sylpheed]("http://en.wikipedia.org/wiki/Sylpheed")

Let us know about moving email boxes and stuff when you do the switch! :D 
madmaxx

---

### Post by krus on 2007-01-11
No solution yet for me... anyone?

---

