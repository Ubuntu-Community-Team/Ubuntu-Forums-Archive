---
title: "Evolution and Microsoft Exchange problem"
date: 2007-03-01
forum: Desktop Environments
---

### Post by AKG on 2007-03-01
Hi, I know there's a lot of information out there on using Evolution for exchange server mail, but I still seem to be having problems at the authentication stage of the account setup.

in account setup you enter [domain\user_name] for your user name, and the appropriate URL for OWA URL. But I know for a fact that my company's OWA URL (webmail.panasonic.com) asks for my entire email address before giving me a pop-up to enter my user name and password. Could this be why my authentication fails? Do other company's OWA URL ask for the email address first also?

Any help is much appreciated.

---

### Post by sanicki on 2007-03-01
Try [https://webmail.panasonic.com/exchange](https://webmail.panasonic.com/exchange) or [http://webmail.panasonic.com/exchange](http://webmail.panasonic.com/exchange). If neither work try them again dropping the domain from the front of username.

---

### Post by AKG on 2007-03-01
Thanks for the advice.   But it still doesn't work.

---

### Post by blockcipher on 2007-03-01
Quick question.  Do you have a windows computer setup with Outlook?  If you setup RPC over HTTP in Outlook does it work?

Seems they are not using "forms based authentication" and that might tweak it.  Because it should show up like this:

[https://exchange.1and1.com/](https://exchange.1and1.com/)

See how you have the form type login there?

---

### Post by airtonix on 2007-03-01
further failing that you can simply use the web interface for the exchange server...

it works fine in firefox and i have a few people using that as they have there browser open anyway.

---

### Post by sanicki on 2007-03-02
...and if you use IEs4Linux and Firefox plugin IEView you can still for the most part get the prettier OWA working.

---

### Post by AKG on 2007-03-02
Yeah, I think our IT people messed with the interface so it doesn't work with Evolution.   It's a shame.  I'm just gonna have to use webmail or a Windows machine for email.

Thanks for all of your help, guys.  I can't wait til there's a linux email client that actually works with Microsoft Exchange (not just OWA).

---

### Post by blockcipher on 2007-03-02
No problem :)

---

### Post by rcmullins on 2007-04-06
I am getting a similar problem when connecting to exchange.  I can download emails, read them, etc. etc.  But I cannot send anything through at all.  Here is the error;

"Your account does not have permission to use <myemailhere> as a From address."

I thought maybe it was my Ubuntu log in identity that needs permission, but I'm not sure.

Any help would be appreciated.

---

### Post by rcmullins on 2007-04-06
Well, looks like it was my mistake.  Sorry for mis-posting. I did a bonehead.

---

