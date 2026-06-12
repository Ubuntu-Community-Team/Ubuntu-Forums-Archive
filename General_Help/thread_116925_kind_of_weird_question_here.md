---
title: "kind of weird question here"
date: 2006-01-13
forum: General Help
---

### Post by harty83 on 2006-01-13
Is there a server that will check and download mail from multiple pop accounts, then allow a client to connect to it and download mail from it?

Reason I ask is that I want to use my desktop as my main pc, but I use my laptop enough that I don't want to have two email clients checking email and me having to sort through them twice.  So I thought I would have the desktop check all my emails, then I download the mail from my desktop.

---

### Post by deNoobius on 2006-01-13
On the server side, fetchmail can retrieve mail from multiple accounts.  I use it successfully with gmail, yahoo mail, and earthlink mail.  It will not work, as far as I know, with hotmail.  You use postfix (there are others as well) to transfer the mail to your client.  You can run fetchmail as a daemon to operate in the background every x number of seconds (e.g., 300 is every 5 minutes)

On the client side, I only use it with one client on one computer, but I'm pretty sure you can use it to serve mail to your network.

The fetchmail documentation is good--it is not hard to configure.  


[http://www.catb.org/~esr/fetchmail/](http://www.catb.org/~esr/fetchmail/)

---

