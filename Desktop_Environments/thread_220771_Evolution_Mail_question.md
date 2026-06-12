---
title: "Evolution Mail question"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Michiba on 2006-07-22
Hi all,

When I try to empty my deleted folder I get the following message:-

ERROR WHILE EXPUNGING FOLDER
Error storing `~/.evolution/mail/local/Inbox (mbox)': Summary and folder mismatch, even after a sync


Is this repairable ??? do I uninstall and reinstall, or is there a easy solution?

Thanks in advance

Michiba

---

### Post by philippe_carlo on 2006-07-22
No idea. I've had situation like this before and so far, I always managed to solve them by restarting evolution.

---

### Post by philippe_carlo on 2006-07-22
No idea. I've had situation like this before and so far, I always managed to solve them by restarting evolution.

---

### Post by philippe_carlo on 2006-07-22
Wow, what's going on here?

---

### Post by Michiba on 2006-07-22
It doesn't seem to matter how many times I restart evolution, the same thing keeps happening.

I now have a large amount of deleted emails.

Uninstall,,,, then re-install???

Michiba:rolleyes:

---

### Post by HushTheVoices on 2007-01-10
Hi I've suddenly started getting the same problem when trying to empty my deleted items folder.  Any idea's?  I'm using version 2.8.1 and Edgy Eft 6.10

---

### Post by helliewm on 2007-01-10
Try a forum dedicated to email [www.emailaddresses.com/forum](www.emailaddresses.com/forum). All the email experts are over at that forum and will be able answer this question. They do not deal with Windows issues but also Linux too. 

Helen

---

### Post by dcstar on 2007-01-10
> **HushTheVoices said:**
> Hi I've suddenly started getting the same problem when trying to empty my deleted items folder.  Any idea's?  I'm using version 2.8.1 and Edgy Eft 6.10

Deleting any corrupted summary files in the Evolution sub-folder usually isn't a problem as they seem to be recreated when you restart Evolution and access the particular folder for the first time.

You may want to move any of the problem summary files to a safe location, restart the Evolution client and see if the problem is fixed.

---

### Post by LineOf7s on 2007-01-10
Close Evolution and then delete the file

**~\.evolution\mail\local\Inbox.ev-summary**

When you next start Evolution it will recreate this file.  This should fix your mismatch problem.

I had a similar problem a couple of days ago.

---

### Post by HushTheVoices on 2007-01-11
Thanks for the responses.  I also found this [http://lists.ximian.com/pipermail/users/2004-April/013505.html](http://lists.ximian.com/pipermail/users/2004-April/013505.html) today, which I think is a variation on what dcstar and LineOf7s have said, but bearing in mind that post is dated 2004, I think I'll give dcstar's go first and if it fixes it, I'll delete them as per LineOf7s post.

Thanks again.

---

### Post by HushTheVoices on 2007-01-14
For some reason getting rid of the summary files didn't work.

Out of frustration, I installed Thunderbird and after a bit of delving on these forums, copied across the e-mails and addressbook and it's all working perfectly....which is nice :D

---

