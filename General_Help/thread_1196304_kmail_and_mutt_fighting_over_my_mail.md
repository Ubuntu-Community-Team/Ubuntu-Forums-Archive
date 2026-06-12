---
title: "kmail and mutt fighting over my mail"
date: 2009-06-24
forum: General Help
---

### Post by ooolongT on 2009-06-24
I use both kmail and mutt to retrieve mail from the same Gmail account.  I generally prefer mutt, but I sometimes use kmail for things that are not mutt's forte.

Both mutt and kmail run on the same machine, and both fetch email.  What is happening is that if one fetches an email the other will not. I may be way off on this one, but it seems that mutt and kmail are checking at unsynchronized intervals, and whichever client checks first downloads the email.  The client that checks second does not fetch that message because the other mail program one has already gotten it.  

That means I have to check two places to make sure that I have all of my email, and what I would like is for all email to go to both places.

---

### Post by whitethorn on 2009-06-24
What are you using to retrieve your emails?  POP3 or IMAP?  If you're using POP3, then the emails will be downloaded locally, which means whichever client is faster will download it.  If you use IMAP, you only download the headers from the emails and when you click on an email, then it'll be downloaded, that way the emails remain on the server which lets you use different clients from different pcs / OSs and still access your email.

---

### Post by ooolongT on 2009-06-24
It sounds like using POP3 may be part of my problem, so I will look into switching to IMAP.  However, I also use both clients to check pop3 hotmail accounts and I do not have the same problem with them.  Is there a reason that gmail's pop3 is behaving differently than hotmail's pop3?

---

### Post by whitethorn on 2009-06-25
I'm not sure if it works with gmail.  Some POP3 accounts lets you leave a copy on the server (an option either on the server or in your client).  But if your using Gmail then I would suggest using Imap.  Unless you plan on carrying your emails with you on a usb stick / want to keep your emails on your laptop to read when you have no internet connection.

---

