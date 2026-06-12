---
title: "Problems with evolution"
date: 2008-12-05
forum: General Help
---

### Post by GrumpyBob on 2008-12-05
I'm using evolution 2.24.2 on Intrepid.  This is a fully updated evolution, and I use it to access email from an Exchange server.  It's worked pretty much flawlessly through several versions.

Lately however, it seems to be behaving oddly: occasional messages don't show up in evolution (but do through Outlook web access).  

Anyone else seeing this?  Is there a solution?

I really can't keep using evolution if I cannot be certain that I can actually see all the emails sent to me!

Robert

---

### Post by utnubuuser on 2008-12-05
Haven't experienced any kind of difficulty, but could it be that your bogofilter is filtering messages?
Preferences>>Plugins>>Bogofilter

---

### Post by GrumpyBob on 2008-12-05
I've diabled the bogofiter plugin - disappeared messages don't reappear, but I will see if the problem has gone for future emails...

R

---

### Post by john.adey on 2008-12-31
I have had the same problem and I found that suddenly Evolution was putting all incoming emails in the junk folder.

Regards

---

### Post by Grosser on 2009-01-15
I had the same problem and found the solution at the last reply - thanks.

---

### Post by dcstar on 2009-01-15
> **john.adey said:**
> I have had the same problem and I found that suddenly Evolution was putting all incoming emails in the junk folder.


Has anyone tries "training" Bogofilter by making all the e-mail in their Junk folder as "Not Junk"? There is a bug where the lack of a certain file stops Bogofilter working correctly, but doing this apparently fixes it:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/282734](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/282734)

---

### Post by Saghaulor on 2009-01-27
My problem is that Evolution is no longer recording messages that I have successfully sent.

They go into the outbox, and then they disappear.

Any ideas?

---

