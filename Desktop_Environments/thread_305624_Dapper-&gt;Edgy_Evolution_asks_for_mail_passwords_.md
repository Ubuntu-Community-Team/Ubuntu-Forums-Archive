---
title: "Dapper-&gt;Edgy: Evolution asks for mail passwords at startup (not a keyring issue ?)"
date: 2006-11-23
forum: Desktop Environments
---

### Post by zorba on 2006-11-23
Hello, 

 I gave up with this issue. Maybe someone could help ?

Issue:

After upgrading from Dapper to Edgy everything seem to look fine, exept Evolution. Always, when evolution starts up, it asks for every password for each configured email account. (standard email password form). It doesn't ask for keyring password. Hitting OK with remember checkbox checked does not resolve the issue (evolution keeps asking for a password). After clicking n times CANCEL (n - accounts count) evolution enters it's main loop (normal functioning) then when I click the "SEND & RECEIVE" button, it gets all the mail (without asking for a password). 

What could be wrong ? How could i configure this thing ? It's quite annoying.

Thanks for help.

---

### Post by dcstar on 2006-11-23
> **zorba said:**
> Hello, 

 I gave up with this issue. Maybe someone could help ?

Issue:

After upgrading from Dapper to Edgy everything seem to look fine, exept Evolution. Always, when evolution starts up, it asks for every password for each configured email account. (standard email password form). It doesn't ask for keyring password. Hitting OK with remember checkbox checked does not resolve the issue (evolution keeps asking for a password). After clicking n times CANCEL (n - accounts count) evolution enters it's main loop (normal functioning) then when I click the "SEND & RECEIVE" button, it gets all the mail (without asking for a password). 

What could be wrong ? How could i configure this thing ? It's quite annoying.

Thanks for help.

Possibly your Evolution setup has got itself corrupted.

Rename the (hidden) .evolution folder in your Home directory, and then restart Evolution so it creates a fresh profile for itself.

Then set up your mail account and see if the problem is now fixed. If it is, you can manually copy all of your previous mail messages from the renamed folder into the new one.

If it doesn't fix the problem, then delete the new .evolution folder and rename the old one back to the original name.

---

### Post by zorba on 2006-11-27
> **dcstar said:**
> Possibly your Evolution setup has got itself corrupted.

Rename the (hidden) .evolution folder in your Home directory, and then restart Evolution so it creates a fresh profile for itself.

Then set up your mail account and see if the problem is now fixed. 

The simplest solution is the best one. You're right. Errors were with .evolution/mail/config directory. After deleting this, evolution got back to normal. Thanks for an answer !

---

