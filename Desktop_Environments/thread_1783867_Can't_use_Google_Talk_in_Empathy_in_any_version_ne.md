---
title: "Can't use Google Talk in Empathy in any version newer than Lucid"
date: 2011-06-16
forum: Desktop Environments
---

### Post by Over the Pond on 2011-06-16
For some time, I've been having a problem with Empathy in versions of Ubuntu newer than Lucid (and hence, versions of Empathy newer than 2.30.3).

When I try to connect to my Google Talk account (which is a Google Apps for your Domain account) it just doesn't do anything. After I enter my username and password and add the account, I don't get an error, or a time-out, it will just say "Connecting..." indefinitely. I once left it all day while I went to work, and came home and it still claimed to be connecting! 

All other IM networks I've tried (AIM and MSN) work perfectly, and Google Talk works perfectly on Empathy 2.30.3 under Lucid. But I'm a heavy Google Talk user, and this error has stopped me upgrading to anything newer than 10.04.2 LTS. 

Searching online for the issue has been fruitless, so does anyone have any clues as to what might be causing it, so I can join the rest of the Ubuntu world in upgrading? 

(I should add that this isn't a Ubuntu-specific issue. I tried the latest Fedora 15 with GNOME 3, and had the same issue with Empathy 3.0.1 in that distribution. But I'm a long-time Ubuntu user since Edgy Eft, so I'm posting here!)

---

### Post by Geoff918 on 2011-06-22
This post worked for me.

> **04 April 2011**

                         ** Troubleshooting failed login to GTalk in Empathy 2.30.3 **

   
  Alright, I just wanna make it quick:
- Check "Ignore SSL certificate errors"
- Uncheck "Encryption required (TLS/SSL)"
- Use "443" as port
- Check "use old SSL"

OK, that's it people...it works for me, hopefully it works for you too. Cheers...

regards,

Mulyadi Santosa 

Copied from [http://the-hydra.blogspot.com/2011/04/troubleshooting-failed-login-to-gtalk.html](http://the-hydra.blogspot.com/2011/04/troubleshooting-failed-login-to-gtalk.html)

I copy-pasted the information in case the link goes dead. This worked for me. If it works for you, please mark this thread "SOLVED".

Thank you,

Geoff

---

### Post by Over the Pond on 2011-06-27
> **Geoff918 said:**
> This post worked for me.



Copied from [http://the-hydra.blogspot.com/2011/04/troubleshooting-failed-login-to-gtalk.html](http://the-hydra.blogspot.com/2011/04/troubleshooting-failed-login-to-gtalk.html)

I copy-pasted the information in case the link goes dead. This worked for me. If it works for you, please mark this thread "SOLVED".

Thank you,

Geoff

Thanks for your help, but unfortunately this just results in an immediate "Disconnected - network error."

---

