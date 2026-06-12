---
title: "emailserver problem"
date: 2009-02-26
forum: General Help
---

### Post by Wudycool on 2009-02-26
Hi there my first post;).
i have a problem with outlock an an ubuntu email server.
i allways get error 0x8000ccc0e.
so, my server has ubuntu 8.10 installed, there is postfix and dovecot running althouth squirrelmail the ports 25 and 143 are open. i try outlock with imap. the filesystem is maildir. squirrelmail works fine from all over the world but outlock doesnt -.-
so ask my what u need to know to solve this problem. i will answer!
Thank u guys!

---

### Post by lotsofish on 2009-02-26
Maybe you could be getting this error because your ISP doesn't allow connections to other third party SMTP servers?

I would try configuring postfix to route all mail through your ISP's smtp servers and see if that works.

Ref: [http://support.microsoft.com/?kbid=302339&sd=RMVP](http://support.microsoft.com/?kbid=302339&sd=RMVP)

---

### Post by HermanAB on 2009-02-26
Go to the Dovecot project web site and start reading.  They have specific workarounds for Outlook bugs.

Cheers,

Herman

---

### Post by T.J. on 2009-02-26
Are you having problems sending or receiving?

Everything with Squirrelmail is local to the server itself so it doesn't have to jump through as many hoops as Outlook does.  Most people using Outlook have problems sending, I'm guessing that you are experiencing.  Sending is has nothing to do with IMAP or Dovecot.  That's SMTP, and likely Postfix on your server. You will need to look at the authentication method that you are using.

If Outlook cannot authenticate itself to Postfix, you will simply get an error.  You will need to check your Postfix configuration as well as your Outlook settings to make sure that they match up.  

If you can't access the IMAP folders at all, then it is likely that you have the Outlook settings on the wrong port, secure authentication enabled in Outlook, or you need to look at your SSL/TLS settings.

Can you please tell me more - as in when you get the error, and I might be able to give you a clearer answer?

---

