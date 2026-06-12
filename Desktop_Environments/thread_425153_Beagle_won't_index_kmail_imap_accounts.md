---
title: "Beagle won't index kmail imap accounts"
date: 2007-04-27
forum: Desktop Environments
---

### Post by monstermunch on 2007-04-27
Hi,

I've just installed Beagle on my Feisty Kubuntu box. It has indexed my files and searching works great. However, it does not seem to have indexed my imap account I have in kmail. If I search for things that are in my imap account in Kerry, it comes up with no emails. It does however index my local inbox. If I copy some emails over from imap to my local inbox, they appear in my search results.

When I run beagle in debug mode I get this message saying it has found where my local mail is stored:

"Debug: Guessing location of KMail folders: found at /home/me/.kde/share/apps/kmail/mail"

Data for my imap accounts seems to be stored in this directory:
"/home/me/.kde/share/apps/kmail/imap"

Does anyone know why my imap account is not being indexed and how to fix it?

Thanks.

---

### Post by monstermunch on 2007-05-01
Does anyone have any idea at all of what I can try? I've asked on answers/launchpad and on the beagle mailing list but have had no reply. :-(

I found out how to set kmail to use disconnected/offline imap. I thought beagle would work with this but it didn't.

---

### Post by ChiaJesus on 2007-05-02
Nope, it doesn't. :)

---

### Post by monstermunch on 2007-05-02
Are you saying it doesn't work with even disconnected IMAP? As far as I know, it works in Evolution.

If this is the case, I suppose I could write a script/filter to copy new mail from my IMAP to my local inbox so that beagle can index it. It's a bad solution though. :-(

---

### Post by ChiaJesus on 2007-05-02
I don't think it's supported...right now. I was poking around a couple of weeks ago and didn't find any way to enable it. All things being equal, I'm sure that the developers will implement it at some point. I think it would be an excellent feature.

---

### Post by monstermunch on 2007-05-03
Wohoo, I got it to work! Open kmail, remove your imap account, add it back and make sure you select "disconnected imap". Close kmail and reopen, click on your inbox and wait for your inbox to be downloaded. Beagle should eventually index your emails.

---

### Post by dbera on 2007-05-10
> **monstermunch said:**
> Does anyone have any idea at all of what I can try? I've asked on answers/launchpad and on the beagle mailing list but have had no reply. :-(

I found out how to set kmail to use disconnected/offline imap. I thought beagle would work with this but it didn't.

You did ??? Seriously, I don't remember seeing it there. Anyway, glad you found the fix. Yes, beagle only indexes "disconnected imap" - the other imap option does not store the email locally so beagle does not index them (and has no plans to do so in the future unless someone sends a patch).

---

