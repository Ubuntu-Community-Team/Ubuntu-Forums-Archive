---
title: "Problems with Evolution sending mail"
date: 2009-10-12
forum: Desktop Environments
---

### Post by unchienne on 2009-10-12
First let me say that I am an absolute newbie to Linux, so please be patient and kind if I ask questions that seem to border on the ridiculous. And yes, I'm going through the tutorials, but I'm also fiddling and playing with everything as a hands-on approach helps me learn faster than just reading alone.

Oh, and I'd also like to add that so far the experience has been fantastic. I had a few rough starts (running u torrent through wine...I'm still not completely sure what a shell is...then changing completely to ktorrent and learning about ports and such), but there's been tons of info out there to help. This OS is structured so well that with little to no computer experience, I've been able to run applications I've never even heard of just by following directions.

Sorry...but I'm excited and had to throw in some praise.

Back to the problem at hand: I set up evolution with my email info (POP/SMTP) and thought all was fine. I received mail with no problem. Actually sent a couple of letters as well. There was an annoying message that kept popping up periodically asking for both my email password and a keyring/keychain/keyguard...something...password as well. But everything worked fine. Now, however, though I can receive mail just as before, evolution won't send any messages. No error message or anything like that...it just tries and tries and tries but nothing happens. And I'm just sending a letter. No attachments. No files.

Any ideas what could be wrong?

I have ATT service and their Pop3 is pop.att.yahoo.com and SMTP is set at smtp.att.yahoo.com

---

### Post by unchienne on 2009-10-12
I don't know why, but now it's working again. I changed the settings, then set them back, and now it works. 

Go figure

---

### Post by donato roque on 2009-10-12
Evolution will try to remember your passwords for you and stores them for you using a password/encryption application called Seahorse.  Seahorse can be accessed by going to Applications>Accessories>Encryptions and Password Keys.  Seahorse will synchronize with a default (if you do not have one of your own) server at a later (convenient) time.  Passwords are kept in a password keyring (folder).  There is an option to lock this keyrings with another password (master password, of sort)
Note:  There is a separate entry (password) for incoming mail and for (SMTP) outgoing mail.

---

