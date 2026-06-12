---
title: "Emptying deleted items in Evolution"
date: 2010-05-28
forum: Desktop Environments
---

### Post by jeffneedle on 2010-05-28
Hello.  I'm using Evolution, latest version for Linux.

For some reason, I can't get the deleted items folder in the mail view to expunge.  Is there some reason why emptying the trash suddenly doesn't work?  It worked for the first few days of using Evolution, but now it just doesn't work -- the deleted items just stay there.

Here's the error message:
Error storing '~/.evolution/mail/local/Handle Later (mbox)': Error storing '~/.evolution/mail/local/Sent (mbox)': Error storing '~/.evolution/mail/local/Inbox (mbox)': Summary and folder mismatch, even after a sync

Any ideas?  Thanks!

---

### Post by hok00age on 2010-05-28
> **jeffneedle said:**
> Hello.  I'm using Evolution, latest version for Linux.

For some reason, I can't get the deleted items folder in the mail view to expunge.  Is there some reason why emptying the trash suddenly doesn't work?  It worked for the first few days of using Evolution, but now it just doesn't work -- the deleted items just stay there.

Here's the error message:
Error storing '~/.evolution/mail/local/Handle Later (mbox)': Error storing '~/.evolution/mail/local/Sent (mbox)': Error storing '~/.evolution/mail/local/Inbox (mbox)': Summary and folder mismatch, even after a sync

Any ideas?  Thanks!
if I were you, I would delete my ~/.evolution folder and get Evolution back in default settings.
:)

---

### Post by jeffneedle on 2010-05-28
This scares me.  Will I lose my contacts and other information?  Sorry about my unfamiliarity with Evolution and Linux.

---

### Post by hok00age on 2010-05-28
> **jeffneedle said:**
> This scares me.  Will I lose my contacts and other information?  Sorry about my unfamiliarity with Evolution and Linux.

Of course, you must back your personal informations up first :)

---

### Post by hictio on 2010-05-28
What type of account is this? Is it POP3 or IMAP?

---

### Post by jeffneedle on 2010-05-29
It's a pop3 account.

---

### Post by hictio on 2010-05-29
Being using Evolution as my Linux email + calendar + contacts app for years now, and maybe it is because I use IMAP, but I've never saw that error myself.
Found this, perhaps you already found it yourself: [evolution: Error while expunging folder](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524363)

---

### Post by hok00age on 2010-05-29
I switched to Thunderbird just now mate! Evolution gives me fatal error, because it can't start anyway. :(

---

### Post by jeffneedle on 2010-05-29
Hictio, I read the page you referred me to, tried the fix suggested, and it worked!

Thanks so much!

---

