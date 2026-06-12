---
title: "Evolution Exchange Error: permission to use from address"
date: 2006-10-23
forum: Desktop Environments
---

### Post by TimJ on 2006-10-23
Hi anyone who can help. I've searched around and not been able to find anything that answers this problem so here goes. I've set up Evolution to connect to my work Exchange server. It finds everything fine but when I try to send mail it comes up with the error:

Error While Performign Operation: Your account does not have permission to use <my email address> as a From address.

And it does not seem to send my mail. I can send using Exchange via the web/owa interface or when I have to use MS-XP and Outlook at work. Any ideas what is blocking Evolution?

---

### Post by lymfnode on 2006-10-23
This is what fixed a similar problem for me:

1) Go into contacts
2) Access your contacts
3) If it asks for password, enter and click "save password"

Try entering the from and to addresses again and it should work... As far as whether or not Evolution maintains the password throughout each session, I'm not sure as I just installed it and am beginning to use it after a long time of not using it... I do, however, remember hearing that was an issue some time ago regarding sustaining the password throughout closing and openning Evolution...

Perhaps they'll fix it soon?

Who knows ;)

Good luck!

---

### Post by TimJ on 2006-10-23
Thanks a lot, I tried that out. Sadly it didn't work. However, it may have helped as I noticed that Evolution put the emails I tried to send into the Outbox on a pop3 account (for the same email account as I'm trying to get to work with Exchange) outbox. This seems kind of weirdly like it's trying to send with one account when I'm using the exchange account. I'm contemplating removing the pop3 account but as it's my fallback I'm reluctant.

---

### Post by maheshjagadeesan on 2007-04-10
I'm faced with the same problem, though in my case the mails do get sent. Just this morning, something occurred to me - I'm going to try an alternate OWA URL. I'll let you know if it worked

---

### Post by maheshjagadeesan on 2007-04-10
I don't know how or why, but thanks lymfnode, your suggestion worked!

Darn software!

---

