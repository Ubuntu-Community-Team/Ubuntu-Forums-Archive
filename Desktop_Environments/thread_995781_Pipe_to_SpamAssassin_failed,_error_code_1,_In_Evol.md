---
title: "Pipe to SpamAssassin failed, error code 1, In Evolution Mail"
date: 2008-11-28
forum: Desktop Environments
---

### Post by clyde9999 on 2008-11-28
I keep getting an error message in Evolution Mail. 

> Pipe to SpamAssassin failed, error code 1

Yet, the filter appears to be working fine. It is indeed filtering junk mail. I use SpamAssassin because Bogofilter simply does not filter out my junk mail.

I have an IBM NetVista 2.4 Gig Hz CPU. 
OS: Ubuntu 8.10 Intrepid Ibex
Network: Cable through a router.

Thanks Much!!

Clyde9999

---

### Post by hictio on 2008-11-28
Check [here](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/282734), maybe the solution will apply to Spamassassin as well?
This solution worked A Ok for me:

> 
Bogofilter will automatically create this file when a message is marked as "Junk". So, as a simple fix, simply mark a message as "Junk" inside of Evolution. You can then go to the Junk folder and mark the message "Mark as Not Junk" if desired. The wordlist.db file will remain in place.


But, then again, I did not had that Spamassassin error message, but the same one on Bogofilter.

And 2 reports on your specific problem:

[Failed spamassassin pipe on Evolution (Intrepid)](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/275746)
[Pipe to SpamAssassin failed, error code: 1](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/281807)

---

### Post by clyde9999 on 2008-11-29
Okay, I have gone both ways to create the folder. Next time I get mail, I will let you know if it  worked.

clyde9999:popcorn:

---

### Post by hictio on 2008-11-29
> **clyde9999 said:**
> Okay, I have gone both ways to create the folder. Next time I get mail, I will let you know if it  worked.

clyde9999:popcorn:

Can't you send yourself an email from a webmail account? :)

---

### Post by clyde9999 on 2008-11-29
Did it, same issue still exists.

clyde99999

---

### Post by cheetaux on 2008-12-03
I get the same error "Check Junk Failed" with the SpamAssassin error code.  This only started with Intrepid.

---

### Post by clyde9999 on 2008-12-10
> **cheetaux said:**
> I get the same error "Check Junk Failed" with the SpamAssassin error code.  This only started with Intrepid.

I still do not have the answer, but am seeking in several locations. Once it is solved, I will make sure to post it here if I did not get the answer here. 

clyde9999

---

### Post by sstidhem on 2008-12-20
I'm getting the same problem and not getting any spam stopped.  I'm migrating from Outlook and I've got a ton of spam to train it with.  I've installed spamd and it's running.

Anybody figure out the fix?  Wifey's getting PO'd at all the spam and is pushing to move back to Windoze.

Ubuntu 8.10
Evolution 2.24.2

---

### Post by momist on 2008-12-30
> **cheetaux said:**
> I get the same error "Check Junk Failed" with the SpamAssassin error code.  This only started with Intrepid.

Mine reports SpamAssassin error code 5.

This only started for me with the upgrade to Intrepid last Saturday.

---

### Post by oldos2er on 2008-12-30
> **cheetaux said:**
> I get the same error "Check Junk Failed" with the SpamAssassin error code.  This only started with Intrepid.

 Just wanted to add a "me too." I have both SpamAssassin and Evolution starting up when the system boots; AFAICT SpamAssassin is running before Gnome loads, so it shouldn't be a timing conflict.

---

### Post by forrestcupp on 2008-12-31
The SpamAssassin package is not installed by default.  It's possible, you're trying to use it when it's not installed.  Evolution does show the SpamAssassin choice even when it's not installed.

```
sudo apt-get install spamassassin
```

---

### Post by william_nbg on 2009-01-02
I'm getting the same error message:

I had been using 8.10 with no issues, but I bought myself a new computer over the holidays and did a fresh install of 8.10 and starting getting the error message - damn if I can understand that.

---

### Post by Tuishimi on 2009-01-09
Same here.  Sometimes it works... but I am getting the same "Pipe to SpamAssassin failed, error code: 1".  And yes, SpamAssassin is installed.  :P

But as another poster mentioned, I empty junk on every exit of Evolution... I just checked when I started it up and got that error and there are junk messages from this morning in the junk mail folder.  It SEEMS to be working.  The error message[s] are annoying tho'. 

Also, in settings, I do have SpamAssassin trying to work out spam using "Remote Tests."  Don't know if that matters.

---

### Post by Mozork on 2009-01-09
That's the strange part, the filtering seems to be working but there still is an error message.

---

