---
title: "[SOLVED] Kubuntu screen saver wouldn't unlock?"
date: 2006-04-21
forum: Desktop Environments
---

### Post by RavenOfOdin on 2006-04-21
Hi. . .I just saw something a little out of the ordinary after coming back to a comp that was on screen saver for 20 mins - It wouldn't unlock, even after I had typed the correct password in about 6 times.

I haven't had anything extremely bad happen, as what I consider to be a full security sweep would attest, but there was an entry which caught my eye:

> 
04/21/2006 08:09:03 PM	localhost	kcheckpass[13666]	Authentication failure for rgandy (invoked by uid 1000)

04/21/2006 08:09:03 PM	localhost	kcheckpass	(pam_unix) authentication failure; logname= uid=1000 euid=1000 tty=:0 ruser= rhost=  user=rgandy

04/21/2006 08:09:03 PM	localhost	unix_chkpwd[13667]	check pass; user unknown


??

That's the first time this has happened to me.

Should I be more than a little concerned, or would this just be a bug in KScreenSaver, and simple matter of "uncheck 'require password after x mins'?"

---

### Post by Parkotron on 2006-04-25
This has happened to me on a couple of occasions as well. I have no idea what caused it, but for the life of me I couldn't get it to accept my password. The first time I was able to "fix" the problem by starting a new session and switching back to the first. This didn't work the second time however. It was ridiculously frustrating.

---

### Post by Mau on 2006-04-25
This happened to me too -- I just lit it sit a little longer, and it worked fine.  I turned off screen savers since then.

---

