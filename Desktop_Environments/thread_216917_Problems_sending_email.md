---
title: "Problems sending email"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Phil196949 on 2006-07-16
Hi, 
I am having problems sending email in all my email clients. (Thunderbird, Mutt, Kmail, and Evolution) I have configured them all according to my isp's recomendations. I also confirmed that the problem wasnt the isp by sending myself an email via Windows XP and had no problems. Is there anything that I might be missing? thanks

Also, my email client seems to connect very slow.

---

### Post by adam.tropics on 2006-07-16
A little more information, such as what client you would like to use, what server you are trying to use etc etc. would be helpful. But normally this is found to be about either incorrect server details, or, and more likely, incorrect security settings.(in mail account/outgoing server settings.

---

### Post by Phil196949 on 2006-07-16
I prefer the Mozilla Thunderbird client. I am trying to connect to earthlink.net (smtp.earthlink.net/mail.earthlink.net)

---

### Post by william_nbg on 2006-07-16
I just started having the same problem today. I can't send mail with evolution or thunderbird. I get this error message in evolution:

Error while performing operation.

DATA command failed: Requested action aborted: error in processing

Anybody else having this problem - yesterday it worked fine.

---

### Post by adam.tropics on 2006-07-16
> **Phil196949 said:**
> I prefer the Mozilla Thunderbird client. I am trying to connect to earthlink.net (smtp.earthlink.net/mail.earthlink.net)

On looking at earthlink.net, it appears that your outgoing server should be

```
smtpauth.earthlink.net
```

with your full email address as a userneme and email password as well, your password! In thunderbird account settings, go to server settings, change the above and set security to use TLS, if available. See if that works.

---

### Post by Phil196949 on 2006-07-16
ok, I have done what you have suggested and still having the same problems. While logging in, my login process hangs for about two minutes then, I get a message stating that it is unable to resolve the server address. The only software that might be interfering is moblock, other than that I am not running any firewalls.

---

### Post by adam.tropics on 2006-07-16
Ok, is it possible to just check the server names from xp as the site (they seem to use a propriatry setup program, so it may not be) is a little unclear, but I do think the security needs to be on as above.

---

### Post by Phil196949 on 2006-07-16
yes I turned on my TLS option and still the same result. :-(

---

### Post by adam.tropics on 2006-07-16
Well I am a bit stuck then, but if you are sure about the server names etc, the only other advice for Earthlink I have found is [this page]("http://www.bu.edu/pcsc/email/remote/smtplist.html") which suggests changing to use port 527. Failing that, try emailing Earthlink for up to date manual settings, just don't mention linux!

---

### Post by william_nbg on 2006-07-16
OK, It was a problem with the server, but the central server just wrote me and told me it was fixed.

---

### Post by Phil196949 on 2006-07-16
I checked with my other pop account, still having the same problem but, my password prompt pops up and then it states that my password is wrong. but I can send mail on XP with my frontiernet.net account

---

### Post by markii on 2007-11-26
I had a problem similar to this recently. I could receive mail but not send (using Evolution for Earthlink account). I had forgotten to allow for SMTP access in Firestarter.

---

