---
title: "Evolution w/Exchange - inbox doesn't stay up to date."
date: 2006-07-05
forum: Desktop Environments
---

### Post by cowmix on 2006-07-05
I am using Evolution that connects to an Exchange 2003 server. A lot of the time I have to exit out of Evolution and then start it up again to make my inbox 'current' to what it should display (like new emails that come in). Hitting the 'Send / Receive" button doesn't cut it. I have 3 instances running that all exhibit the same behavior.

Am I doing something wrong?

BTW.. I know this sounds like a general Evolution question but I figured since I was using the stock Dapper version.. I would ask here first.

---

### Post by jayemef on 2006-07-05
Go to **Edit** > **Preferences**, select an account, and hit the **Edit** button on the right. A new window will appear. Within that, go to the **Recieving Options** tab and check where it says *Automatically check for new mail every __ minutes*, filling in the number of minutes as you deem fit.

---

### Post by cowmix on 2006-07-05
When I first setup all my Evolution clients I set this vaule to 2 min..

So that doesn't seem to work..

Its funny.. 3/4s the time it DOES update fine.. its just sometimes the new mails doesn't show up until I reset..

[QUOTE=jayemef]Go to **Edit** > **Preferences**, select an account, and hit the **Edit** button on the right. A new window will appear. Within that, go to the **Recieving Options** tab and check where it says *Automatically check for new mail every __ minutes*, filling in the number of minutes as you deem fit.[/QUOTE]

---

### Post by jmaest on 2008-01-24
I'm having the exact same issue with a little twist.  The "Inbox" shows the new "unread" emails but they don't actually show up in the Inbox itself until I reset evolution.  There has to be a reason for this.  I've tried the following script, which clears the exchange cache:

#!/bin/bash

if (zenity --question --text="Are you sure you want to do this? It will make evolution very slow on next start.")
then
        evolution --force-shutdown
        evolution --force-shutdown
        rm -rf ~/.evolution/exchange ~/.evolution/mail/exchange
fi

That hasn't made the problem go away, though.

---

### Post by jmaest on 2008-01-25
After messing with this last night I've found that I can recreate this error every single time by switching between Inboxes.  I have four different accounts in my evolution set up.  Three are pop and obviously one is my exchange account.

So long as I stay within my exchange account I have no issues whatsoever.  All mail updates appropriately.  Once I switch to my local Inbox, however, it screws up the exchange account.

I hit this issue each and every single time I do this.

---

### Post by jmaest on 2008-01-30
So after continuing to troubleshoot this issue I found a fix that can be replicated any time.  

1)  Simply log in to your <home>/.evolution directory and 'rm -rf' anything that's not a directory:

2)  Then move to <home>/.evolution/mail and do the same EXCEPT for "filters.xml".

3)  Then move to local, under the current directory, and here 'rm -rf' anything that actually has a file extension.  For example there's "Inbox" and then there's "Inbox.ev-summary".  DO NOT REMOVE INBOX or any files WITHOUT an extension in this directory.

Now I must admit I haven't been able to put together why this works or how much of the above is overkill, although I have a number of theories.

What I do know for sure is that the above absolutely works.

---

### Post by sockrebel on 2008-02-14
I have the same issue.  Staying in my exchange account = no issues.  If I receive mail (in exchange) when I'm viewing a local Inbox, it screws up the exchange account.

I'm not sure what you mean by "a fix that can be replicated any time"  I still seem to have the same problem after following the instructions below.


> **jmaest said:**
> So after continuing to troubleshoot this issue I found a fix that can be replicated any time.  

1)  Simply log in to your <home>/.evolution directory and 'rm -rf' anything that's not a directory:

2)  Then move to <home>/.evolution/mail and do the same EXCEPT for "filters.xml".

3)  Then move to local, under the current directory, and here 'rm -rf' anything that actually has a file extension.  For example there's "Inbox" and then there's "Inbox.ev-summary".  DO NOT REMOVE INBOX or any files WITHOUT an extension in this directory.

Now I must admit I haven't been able to put together why this works or how much of the above is overkill, although I have a number of theories.

What I do know for sure is that the above absolutely works.

---

