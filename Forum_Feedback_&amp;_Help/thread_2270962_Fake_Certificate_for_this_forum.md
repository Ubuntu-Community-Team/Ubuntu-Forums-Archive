---
title: "Fake Certificate for this forum?"
date: 2015-03-26
forum: Forum Feedback &amp; Help
---

### Post by haplorrhine on 2015-03-26
So anyway, I was starting to force https on this site, which broke many of the unencrypted graphics.  Now the graphics are appearing regardless.  I'm recieving the gray padlock.  Here is the certificate.

> Website Identity:
Website:  ubuntuforums.org
Owner:  This website does not supply ownership information.
Verified by:   GoDaddy.com, Inc.

Privacy and History:
Have I visited this website prior to today?  No
Is this website storing information (cookies) on my computer?  Yes
Have I saved any passwords for this website?  No

Technical Details:
**Connection Encrypted (TLS_DHE_RSA_WITH_AES_128_CBC_SHA, 128 bit keys, TLS 1.2)**
The page youa re viewing was encrypted before being transmitted over the Internet.

GoDaddy.com?  It sounds fishy.  I have visited this site from this browser on this system as this user prior to today.

---

### Post by slickymaster on 2015-03-26
*Moved to the ***Forum Feedback & Help*** sub-forum*

---

### Post by haplorrhine on 2015-03-26
I tried purging and reinstalling firefox, removing the old profiles, and deleting the non-sudo user accounts that I accessed the itnernet with, but it's still there.

edit:  I think the site was having troubling remembering my login when I starting forcing secure cookie management, but it seems okay now even though I'm still forcing secure cookies with NoScript.
I'm just rather dumbfounded.  I remember browsing this site lightly in a reduced https-only format, never recieving any certificates.  Now I can't even open the home page (in https) without getting this certificate, and I can't reject the certificate.  I'm using the Certificate Patrol addon.

---

### Post by user1397 on 2015-03-26
Why would godaddy.com sound fishy? It is definitely one of the main domain name/hosting websites in the world.

---

### Post by haplorrhine on 2015-03-26
I apologize.  I'm brand new to certificate monitoring.  It's funny that I've neglected it up until now!

Do you get that same certificate when you force https?  I wasn't at first.

---

### Post by user1397 on 2015-03-26
> **haplorrhine said:**
> I apologize.  I'm brand new to certificate monitoring.  It's funny that I've neglected it up until now!

Do you get that same certificate when you force https?  I wasn't at first.
No need to apologize!  And yes, I get the same certificate when I force https.

---

### Post by haplorrhine on 2015-04-01
> **ubuntuman001 said:**
> No need to apologize!  And yes, I get the same certificate when I force https.

Thank you, ubuntuman.  It seems that many https certificates have a SHA1 fingerprint / key.  This can be seen by clicking "View Details" when Certificate Patrol notifies you of an incoming certificate, which may or may not be accepted by default depending on the settings.  This is the SHA1 fingerprint on my UF certificate.
D9:2D:FD:1C:E1:AF:38:2B:DD:44:5B:FF:31:1B:90:00:02:1A:B8:67
How do I check its accuracy?

Now this is interesting.  I was getting variable SHA1 keys before, with a brief intermission wherein all new certificates were showing key below.
E4:1A:1C:CE:0E:42:57:6F:F1:2C:E2:0F:13:13:D7:72:CE:64:AF:D3
I just purged/reinstalled firefox and returned under a new firefox profile, and they returned to this SHA1 key again.  But on this session, as far as I can tell from the CP notifications, no other certificates with other SHA1 keys have been sent.
The only two cached GoDaddy certificates I can see via the "advanced" tab have the SHA1 keys below.  It must not be accepting.
27:AC:93:69:FA:F2:52:07:BB:26:27:CE:FA:CC:BE:4E:F9:C3:19:B8
47:BE:AB:C9:22:EA:E8:0E:78:78:34:62:A7:9F:45:C2:54:FD:E6:8B

Could this be a sign of session hijacking, or worse?

---

### Post by user1397 on 2015-04-12
> **haplorrhine said:**
> Thank you, ubuntuman.  It seems that many https certificates have a SHA1 fingerprint / key.  This can be seen by clicking "View Details" when Certificate Patrol notifies you of an incoming certificate, which may or may not be accepted by default depending on the settings.  This is the SHA1 fingerprint on my UF certificate.
D9:2D:FD:1C:E1:AF:38:2B:DD:44:5B:FF:31:1B:90:00:02:1A:B8:67
How do I check its accuracy?

Now this is interesting.  I was getting variable SHA1 keys before, with a brief intermission wherein all new certificates were showing key below.
E4:1A:1C:CE:0E:42:57:6F:F1:2C:E2:0F:13:13:D7:72:CE:64:AF:D3
I just purged/reinstalled firefox and returned under a new firefox profile, and they returned to this SHA1 key again.  But on this session, as far as I can tell from the CP notifications, no other certificates with other SHA1 keys have been sent.
The only two cached GoDaddy certificates I can see via the "advanced" tab have the SHA1 keys below.  It must not be accepting.
27:AC:93:69:FA:F2:52:07:BB:26:27:CE:FA:CC:BE:4E:F9:C3:19:B8
47:BE:AB:C9:22:EA:E8:0E:78:78:34:62:A7:9F:45:C2:54:FD:E6:8B

Could this be a sign of session hijacking, or worse?Not sure honestly, I think this is a bit over my head now! Anyone else care to answer?

---

