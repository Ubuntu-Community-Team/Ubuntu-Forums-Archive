---
title: "Evolution - Fix corrupt mail folders how-to"
date: 2009-03-03
forum: General Help
---

### Post by SwedishWings on 2009-03-03
After having long lasting problems with my evolution mail folders and searching for solutions in vain, i set out to find a way to fix this myself. I have now fixed three problematic installations with no glitches.

If you get error messages like 
 
```
Emptying Trash Fails with 'Error while expunging folder'
```
or
```
Evolution: Summary and folder mismatch, even after a sync
```
or
```
Evolution: Error while Expunging folder
```
or
```
Evolution: error storing '~/.evolution/mail/local/Inbox (mbox)':
summary and folder mismatch, even after a sync.

```
the following solution will most likely work:


1) Stop evolution.

2) Move folder ~/.evolution/mail to desktop.

3) Start evolution. It will create all standard folders again.

4) Stop evolution.

5) Move _only_ the mailbox files (i.e. "Inbox", not the other files like "Inbox.cmeta" etc) under ~/Desktop/mail/local back to ~/.evolution/mail/local. If you have nested levels of folders, re-create the same folder hierarchy and place the mailbox files accordingly.

6) Run '$ evolution --offline'. Evolution will take some time to re-index and update the data base properly. 

7) Restart evolution, and click on the on/off-line button in the lower left corner to get back on-line.

Btw, i use Evolution 2.24.3, but _guess_ that this fix is pretty version independent.

Hope this helps.

PS. If any Evolution developer is reading this: Many postings suggest this is a common problem. Perhaps it would be a good thing to have a "repair" switch that does the above steps in Evolution? DS.

---

### Post by jamie0nz on 2009-03-19
I have had a similar problem, I got more aggressive as time went by in deleting things (taking a suitable backup of course). What appears to have worked is going in to .evolution/mail/local and deleting everything that was not an actual mail file, all the ev-summary / cmeta / ibex files and the folder.db file.

'man evolution' indicates a force update option on the database. My own email I've been using for only about the last 12 months in evolution (since hardy) I wonder if - in cleaning out - I have wiped the old format database and that now the new one is in place (just guessing here - I really have no idea).

---

### Post by Statik on 2009-04-28
I've tried deleting everything but the actual mail files, and it only worked short-term. I've just tried this solution. Lets see how long it lasts. :)

Statik

---

### Post by twl on 2009-04-29
This fix worked for me.  Thank you.

This has been a recurring problem in Evolution for years.  Different solutions have worked at different times (like removing all the *.ev-* files).  I really hope the Evolution developers get a handle on this at some point.

---

### Post by SwedishWings on 2009-04-29
> **twl said:**
> This fix worked for me.  Thank you.

This has been a recurring problem in Evolution for years.  Different solutions have worked at different times (like removing all the *.ev-* files).  I really hope the Evolution developers get a handle on this at some point.

Happy to help :)

---

### Post by Statik on 2009-05-04
Nope, its back. Error while Expunging Folder on emptying trash again. *sigh*

I guess I'm stuck with it.

Statik

---

### Post by happyisland on 2009-11-22
> **SwedishWings said:**
> After having long lasting problems with my evolution mail folders and searching for solutions in vain, i set out to find a way to fix this myself. I have now fixed three problematic installations with no glitches.

If you get error messages like 
 
```
Emptying Trash Fails with 'Error while expunging folder'
```
or
```
Evolution: Summary and folder mismatch, even after a sync
```
or
```
Evolution: Error while Expunging folder
```
or
```
Evolution: error storing '~/.evolution/mail/local/Inbox (mbox)':
summary and folder mismatch, even after a sync.

```
the following solution will most likely work:


1) Stop evolution.

2) Move folder ~/.evolution/mail to desktop.

3) Start evolution. It will create all standard folders again.

4) Stop evolution.

5) Move _only_ the mailbox files (i.e. "Inbox", not the other files like "Inbox.cmeta" etc) under ~/Desktop/mail/local back to ~/.evolution/mail/local. If you have nested levels of folders, re-create the same folder hierarchy and place the mailbox files accordingly.

6) Run '$ evolution --offline'. Evolution will take some time to re-index and update the data base properly. 

7) Restart evolution, and click on the on/off-line button in the lower left corner to get back on-line.

Btw, i use Evolution 2.24.3, but _guess_ that this fix is pretty version independent.

Hope this helps.

PS. If any Evolution developer is reading this: Many postings suggest this is a common problem. Perhaps it would be a good thing to have a "repair" switch that does the above steps in Evolution? DS.



This worked to get my evolution working again. I had seen problems when copying email folders from another computer that had been running Thunderbird. (I switched because I like how evolution works with gnome, not because I think it's necessarily a better program). Anyway, thanks for posting the solution, and I definitely second your emotion on having this repair process built in to evolution going forward. It's a pretty daunting fix that would turn off many people who are beginners and just want their PCs to work.

---

### Post by Stratis on 2010-01-16
This worked like a charm.

Thanks for the thread!

---

### Post by dcstar on 2010-01-16
There is a (slightly) simpler way:

[LIST=1]
[*]Shutdown Evolution client
[*]Rename /home/<your user name>/.evolution/mail/local/folders.db file
[*]Restart Evolution again and now syncs should be successful.
[/LIST]
It seems there is a database listing the various mail box files that can get corrupted, and just deleting the individual cmeta and index files does not fix this up.

This method leaves your Calendar/Contact info intact.

---

### Post by ExpatPaul on 2010-04-06
> **dcstar said:**
> There is a (slightly) simpler way:

[LIST=1]
[*]Shutdown Evolution client
[*]Rename /home/dc/.evolution/mail/local/folders.db file
[*]Restart Evolution again and now syncs should be successful.
[/LIST]
It seems there is a database listing the various mail box files that can get corrupted, and just deleting the individual cmeta and index files does not fix this up.

This method leaves your Calendar/Contact info intact.

You are a lifesaver. I'd been struggling with this all morning until I found you post. Everything seems to be working now.

---

### Post by galpec on 2010-04-15
Thank you guys... it seems this problem has been a sting in many foots, but the EVOLUTION seekers, keep it up....

Now, for me Evolution is the best...


The developers have to be getting this relatively simple solution in their next releases!!


Thank you again I appreciate your efforts...


:guitar:

---

### Post by realmkeeper on 2011-09-08
> **dcstar said:**
> There is a (slightly) simpler way:

[LIST=1]
[*]Shutdown Evolution client
[*]Rename /home/dc/.evolution/mail/local/folders.db file
[*]Restart Evolution again and now syncs should be successful.
[/LIST]
It seems there is a database listing the various mail box files that can get corrupted, and just deleting the individual cmeta and index files does not fix this up.

This method leaves your Calendar/Contact info intact.

Thanks, also got stuck with this one. 

Newer versions store seem to use ~/.local/share/evolution/mail/...

---

### Post by dcstar on 2011-10-07
> **realmkeeper said:**
> Thanks, also got stuck with this one. 

Newer versions store seem to use ~/.local/share/evolution/mail/...

Yeah, I've seen a few reports that the current versions of Evolution have moved that folder.

I have also noticed that using my method of renaming the .db file results in a much smaller new file and it seems to improve Evolution's performance. I just did it on my system and the .db file went from 5.5MB to 178KB!

There are also .db files in the **evolution/mail/imap** tree which may also be renamed if people are having issues with their IMAP connections syncing correctly (apparently a known bug):

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/346352](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/346352)

---

### Post by thepisu on 2012-01-02
I had the same issue with Evolution 3.2.1, and solved deleting the file **folders.db** inside ~/.local/share/evolution/mail/1295611670.31535.6@cvs28.

So now the folders.db is no more in evolution/mail/imap, but in evolution/mail/GUID.

---

### Post by AFD8766 on 2012-02-01
Trying to prevent Evolution from over-fetching when I send/receive.  I guess it wants to grab all messages, old and new.  Tried re-creating folder.db file, per <dcstar> in this thread.  Am considering solution from the initial post <SwedishWings> in the thread.

Full explanation here: [http://ubuntuforums.org/showthread.php?t=1918845](http://ubuntuforums.org/showthread.php?t=1918845)


But: I have two accounts, and only one of the two addresses has this problem.  It's the one with "leave messages on server," in case that matters.  Does this tell me anything??

Update:  I removed the four inbox files from /.evolution/mail/local and fetched mail.  Now fetching only the most recent.  See above other thread for details.

---

### Post by AFD8766 on 2012-05-11
I had the same problem and pursued the same solution.  I updated the other thread.  See there for details.
[http://ubuntuforums.org/showthread.php?p=11926545](http://ubuntuforums.org/showthread.php?p=11926545)

Also posted it to the evolution e-mail list. 
[email]evolution-list@gnome.org[/email]
[http://mail.gnome.org/mailman/listinfo/evolution-list](http://mail.gnome.org/mailman/listinfo/evolution-list)

---

