---
title: "Evolution no longer tries to receive mail (lucid)"
date: 2011-03-15
forum: Desktop Environments
---

### Post by larseko on 2011-03-15
Hi there.

Since Feb 23-24, Evolution (2.28.3) no longer receives any e-mail. When I click send/receive, the usual dialog appears, but finishes real quick, with no messages downloaded. I know there are messages, and Evolution is in online mode. I have tried removing the "remember password" option on all accounts, but evo won't ask for a new password when I try to receive mail. I have tried to delete all accounts from within evolution, and create new ones, but no luck.

All accounts are pop servers, and I have also tried turning pop3 extensions off.

Has anyone got any suggestions as to what is wrong here? 

I'll provide some log files, but will have to clean up usernames, servers etc.

---

### Post by pearlbeer on 2011-03-15
I have the same problem. This started happening out of the blue last week, I have since upgraded to 10.10 and set up Evolution again, and still have the same problem. Mail will send fine, but it just 'flashes' through the receive and doesn't receive any emails.

---

### Post by shafiekd on 2011-03-15
Did you guys try and remove the account from Evolution & set it up from scratch?

Similar issue happens quite often with Outllok Express on windows PC's.....

---

### Post by pearlbeer on 2011-03-15
I just tried that. It flashes "Getting 1 of 17" for a split second and disappears, not receiving any email.

---

### Post by larseko on 2011-03-15
Yeah, I've tried to delete all accounts from within evolution. Should probably export/backup all contacts/mail and wipe the .evolution folder, but I'm so lazy. Was hoping for an easy fix.

---

### Post by pearlbeer on 2011-03-15
I was using 9.04 when it happened and decided it was a good time to upgrade. So I did a fresh install of 10.10 and restored Evolution, and the problem is still there. Let me know if you figure it out, and I'll do the same.

---

### Post by larseko on 2011-03-15
How did you "restore evolution"? Did you just keep the .evolution folder?

---

### Post by pearlbeer on 2011-03-16
I ran "backup settings" before I installed Ubuntu 10.10 then "restore settings" to import all my old mail and contacts. I have since tried to set up a new mail account and still have the same issue, though.

---

### Post by larseko on 2011-03-16
Strange thing. Well, might migrate to Thunderbird for good.

---

### Post by rvchari on 2011-03-16
> **larseko said:**
> Hi there.

Since Feb 23-24, Evolution (2.28.3) no longer receives any e-mail. When I click send/receive, the usual dialog appears, but finishes real quick, with no messages downloaded. I know there are messages, and Evolution is in online mode. I have tried removing the "remember password" option on all accounts, but evo won't ask for a new password when I try to receive mail. I have tried to delete all accounts from within evolution, and create new ones, but no luck.

All accounts are pop servers, and I have also tried turning pop3 extensions off.

Has anyone got any suggestions as to what is wrong here? 

I'll provide some log files, but will have to clean up usernames, servers etc.
i use multiple accounts (pop / imap for yahoo and fastmail)
my pop account had similar problem as it never downloaded ny mail. i guess sometimes a particular long msg (most probably spam) gets jammed. i went to the web mail service of my pop mail and reviewed and deleted unwanted mails and organised everything there.
after cleaning up there, i tried evolution again and i got it working....
wonder what was wrong but as of now it works... can you try the same and revert back ?

---

### Post by larseko on 2011-03-16
I've tried that, and nothing's there. Also, evolution doesn't even prompt for password (I unchecked "remember password"), hence it doesn't even connect.

---

### Post by pearlbeer on 2011-03-16
I've cleaned out the messages on the server, and unchecked the password as well. It never asks for it..just flashes the little download window like it is going to download messages and says failed and disappears.

---

### Post by pearlbeer on 2011-03-16
Also, I have tried to set up 3 different email accounts to verify this wasn't something server side. Same problem with all of them (and they all work in Thunderbird).

---

### Post by pearlbeer on 2011-03-16
larseko-

I just ran Evolution fresh from terminal and set up email WITHOUT restoring. It downloaded emails immediately. Must have received some bad info when I restored settings from previous version. Guess I'll import old contacts and emails separately and go from there.

---

### Post by larseko on 2011-03-16
Good for you. Let me know if it still works when you move email back :)

---

### Post by pearlbeer on 2011-03-17
It did work after i imported email and contacts. Worked all day long yesterday, no problems. Well, this morning, it is doing the same damn thing. Guess it is thunderbird time.

---

### Post by pearlbeer on 2011-03-17
Figured out my problem. ...wait, no i didnt.

---

### Post by pearlbeer on 2011-03-17
Ok. Maybe I did. It is receiving again. Read somewhere that inbox has a 2g limit. I rarely empty/sort my inbox, so I may have breached that. Deleted emails from inbox within evolution email and still wouldnt download messages. Then deleted all the 'inbox' files (there were like 3 of em) under home/evolution/mail/local...rebooted and now it is receiving again. Hope this helps someone down the line.

Note: it did make all the mail in my trash folder disappear, so do a backup first.

---

### Post by larseko on 2011-03-21
Ok, 2GB limut huh? Well, that's it for me. I've moved on to Thunderbird.

Edit: Btw, my .evolution folder is no more than 225MB.

---

