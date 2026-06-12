---
title: "Trash won't empty in Evolution"
date: 2009-05-30
forum: General Help
---

### Post by PaulNKS on 2009-05-30
When I try to "Empty Trash" in Evolution, I get the following error:
[I]
"Error while Expunging folder.

Error storing '~/.evolution/mail/local/Inbox/Authnet (mbox)': Error storing '~/.evolution/mail/local/Inbox/Legacy UG (mbox)': Error storing '~/.evolution/mail/local/Inbox/Fuchsorama (mbox)': Error storing '~/.evolution/mail/local/Inbox/02 Sales (mbox)': Error storing '~/.evolution/mail/local/Inbox/FuchsFriends (mbox)': Error storing '~/.evolution/mail/local/Inbox/FuchsSupport (mbox)': Error storing '~/.evolution/mail/local/Inbox/01 Payments (mbox)': Error storing '~/.evolution/mail/local/Sent (mbox)': Error storing '~/.evolution/mail/local/Inbox (mbox)': Summary and folder mismatch, even after a sync"[/I]

Can anyone tell me how to repair it?  All I can see is that there are errors relating to the sub-folders in my inbox.  However, this is the error message I get when I right click on the Trash folder and try to empty.

Thank you in advance.
Paul

---

### Post by Swagman on 2009-05-30
Your not alone in this.

---

### Post by PaulNKS on 2009-06-02
Anyone have any solution?

---

### Post by dcstar on 2009-06-03
> **PaulNKS said:**
> When I try to "Empty Trash" in Evolution, I get the following error:
[I]
"Error while Expunging folder.

Error storing '~/.evolution/mail/local/Inbox/Authnet (mbox)': Error storing '~/.evolution/mail/local/Inbox/Legacy UG (mbox)': Error storing '~/.evolution/mail/local/Inbox/Fuchsorama (mbox)': Error storing '~/.evolution/mail/local/Inbox/02 Sales (mbox)': Error storing '~/.evolution/mail/local/Inbox/FuchsFriends (mbox)': Error storing '~/.evolution/mail/local/Inbox/FuchsSupport (mbox)': Error storing '~/.evolution/mail/local/Inbox/01 Payments (mbox)': Error storing '~/.evolution/mail/local/Sent (mbox)': Error storing '~/.evolution/mail/local/Inbox (mbox)': Summary and folder mismatch, even after a sync"[/I]

Can anyone tell me how to repair it?  All I can see is that there are errors relating to the sub-folders in my inbox.  However, this is the error message I get when I right click on the Trash folder and try to empty.

Thank you in advance.
Paul

Is the total size of your .evolution folder >2GB?

---

### Post by PaulNKS on 2009-06-08
> **dcstar said:**
> Is the total size of your .evolution folder >2GB?

No.  It's 389MB.

---

### Post by PaulNKS on 2009-06-08
Problem solved.  I finally found the solution in another thread. I first used Evolution File > Backup Settings.

Then I went to my .evolution/mail/local and deleted all files that had an extension of:
.index
.cmeta
but NOT .data
 
When restarted it takes a few minutes to rebuild. Then I was able to successfully delete everything in my trash folder.

---

### Post by undinegreif on 2010-04-13
It works exelent!!

---

### Post by drpjkurian on 2010-06-04
Hi
Try this
```
#!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
done
rm ~/.evolution/mail/local/folders.db
```

---

### Post by 1script on 2011-01-12
> **drpjkurian said:**
> Hi
Try this
```
#!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
done
rm ~/.evolution/mail/local/folders.db
```

Thanks, drpjkurian
Your solution had finally solved my 2+ years of Evolution trash emptying mysteries (at 27,000+ messages in Trash we could also call them miseries :) )

Nothing I've tried before worked until I noticed that your script included a line removing folders.db file which I was afraid to touch before:

```
 rm ~/.evolution/mail/local/folders.db
```

After I saw it in your script, I looked into this file and it looked as if most of its 35MB content was the spam I've been deleting all these years. So, I deleted the file. On the next start Evolution re-created it, and I tried to "Empty Trash" and =D> the trash is gone!

Thanks again!

---

### Post by lesiano on 2011-04-06
> **drpjkurian said:**
> Hi
Try this
```
#!/bin/bash
export LANG=C
set -e
evolution --force-shutdown
tar -zcf dot_evolution_$$.tgz ~/.evolution/
for each in index data cmeta; do
 find ~/.evolution/mail/local -type f -iname "*.$each" | xargs rm
done
rm ~/.evolution/mail/local/folders.db
```


Problem solved. :)
Thank you very much!

---

