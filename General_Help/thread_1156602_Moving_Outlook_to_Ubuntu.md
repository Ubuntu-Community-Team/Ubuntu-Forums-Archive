---
title: "Moving Outlook to Ubuntu"
date: 2009-05-11
forum: General Help
---

### Post by HippieDave on 2009-05-11
I'm sure this has been asked countless times, but I can't find a thread on it. Point me in the right direction!

I just installed Ubuntu and want to migrate my Outlook .pst file, with all my contacts etc in it.  I used Mandriva once, a while ago on another PC, and was able to do it there: but I can't find instructions on doing it into Ubuntu. Help!

---

### Post by trentscott4 on 2009-05-11
Try Outport ([http://outport.sourceforge.net/](http://outport.sourceforge.net/)).

You'd have to run it on Windows, but it would allow you to export the PST file to something compatible with Evolution or Thunderbird.

Alternatively, you could install Thunderbird on Windows, import your Outlook and export the Thunderbird file.

Unfortunately, because Outlook uses a proprietary MAPI format you don't have many other options.  Good luck! :)

---

### Post by Ericyzfr1 on 2009-05-11
The way I did it in the past was to import in Thunderbird so then it can be used also in Evolution.

---

### Post by jflaker on 2009-05-11
If you have gmail, set up gmail's imap capability.  

Set up an imap account to gmail under outlook then move your folders one by one over to gmail.

Set up gmail under thunderbird or evolution then move your folders back...

That is the way I did it.  Depending on how much mail you have and attachments, you may have to work at it a while, BUT, you will be able to keep your emails from the past.

---

### Post by HippieDave on 2009-05-12
Thanks all.  I'll try the Thunderbird approach.

---

### Post by stinger30au on 2009-05-12
there is a version of evolution for windows

[http://www.dipconsultants.com/evolution/](http://www.dipconsultants.com/evolution/)


i have heard of mixxed experiences.

everything from it wont start and its hopeless, to its the best thing since sliced bread

---

### Post by The_Cougar_Kid on 2009-10-15
> **HippieDave said:**
> Thanks all.  I'll try the Thunderbird approach.

I am very new to UBUNTU and I face the same problem.  I tried the THUNDERBIRD approach and got very encouraged - then foiled at the last hurdle!

Install Thunderbird on the Windows machine, set it up, then close it.
Install Mozbackup on the windows machine and run it in BACKUP mode.  It magically collects up all the OUTLOOK PST files and exports them to a single PCV document
Export the PCV file to another PC where you have installed THUNDERBIRD and MOZBACKUP.
Run MOZBACKUP and choose restore.  Hey Presto, all the Outlook folders and their contents have been moved across!

BIG SNAG THOUGH: that process worked fine going from a windows PC to a different Windows PC - BUT there does not seem to be a version of MOZBACKUP for linux....  That is a big SHOW STOPPER and so this method doesn't do what I'm trying to do...

---

### Post by HermanAB on 2009-10-15
The best way to move email is via an IMAP server as suggested above.  Open a gmail account, create an Outlook account and click drag drop the email from the POP account to the IMAP account.  Then repeat in reverse with any other mail client.

---

