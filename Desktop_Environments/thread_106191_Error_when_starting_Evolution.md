---
title: "Error when starting Evolution"
date: 2005-12-20
forum: Desktop Environments
---

### Post by gosh on 2005-12-20
When I start my e-mail client Evolution the following error message appears:



Error while Storing folder 'Inbox'.

Summary and folder mismatch, even after a sync



In my Inbox new messages appear twice.

What causes this?

---

### Post by cstudent on 2005-12-20
Looks like it is telling you simply that your inbox file doesn't match up with your inbox_summary file.

Go to the Places menu>Home Folder and open Nautilus.

Click on View and Show Hidden Files.

Navigate your way to the .evolution/mail/local folder. There you'll see several files concerning your inbox. One called Inbox, another called Inbox-ev-summary.

Copy (not move) your .evolution folder to another location for backup purposes. You could just backup the local directory you were just viewing, but myself, I would feel safer having the whole directory backed up. Then it is a simple matter of just copying the safed folder back into it's proper place.

Next rename the Inbox-ev-summary folder to something like Old-Inbox-ev-summary and then restart Evolution. See if this solves your problem. I experimented with my own Evolution and this method just recreated a fresh Inbox-ev-summary file for me.

---

### Post by gosh on 2005-12-21
Thnx!

That did the trick.
:D 

Gosh

---

### Post by halitech on 2006-03-26
thank you for this, 3 months after the original solve and because of the search, I was able to fix the same problem with my mail without having to start a new thread so, I'll again say thank you and shut up before people start thinking I'm nuts :D

---

### Post by Scunizi on 2006-03-27
That worked great but I had to use a little twist.  After renaming the one file with "old.xxx" I encountered the same problem.  So I renamed the Inbox to Old.inbox and restarted evolution.  It recreated several files all beginning with "Old.xx" It worked except now I had a new folder in Evol. called Old.inbox.  So I renamed Old.inbox to inbox and deleted all the original files using the new "old.xx" files as referance.  After that I just deleted the Old. from the front of the remaining files AND Viola!  No more extra folder in Evolution and everything running smoothly.  Thanks for the help!

NOTE Update:  The problem cropped up again so this time all I did was delete the inbox file.  So far, so good.  Time will tell.

---

### Post by InterNut on 2006-04-21
The way i fixed it is as follows:
closed evo.
in terminal i removed all the ***.ev-summary** files in **/home/username/.evolution/mail/local/**
dont know if that was the correct approach, but it seems to work, atleast here :-D

---

### Post by rcjhawk on 2006-04-25
This works.  So does:

$ find ~/.evolution -name "*summary" -exec ls -l {} ';'

However, this is the third time I've had to clear out my summary files since I installed Ubuntu last month.  There doesn't seem to be any <a href="https://launchpad.net/distros/ubuntu/+source/evolution/+bug/28403"> hurry to fix the problem</a>, either.  (That's a link to Debian's bugzilla, Ximian's doesn't list the problem.)

Thinking of switching to Thunderbird ...

-- 
                                                           mjm
                                                           [http://hawknotes.blogspot.com](http://hawknotes.blogspot.com)

---

### Post by Ux64 on 2007-11-19
Thanks, solved my problem too.

---

### Post by mickthejew on 2008-02-17
Worked for me too!  Thanks so much.

---

### Post by miserabledutchman on 2008-02-28
Ok the above did not work for me, but it somehow brought me to understand the problem as I was having it:

My mail is left on the server after fetching to allow my laptop to catch the mail too.  The laptop is set to leave NO copies.  Here's the killer: I havent been working on the laptop for a good two weeks now, so the messages never got purged from the server.

---

