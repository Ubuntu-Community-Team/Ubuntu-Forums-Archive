---
title: "Cannot access Amazon with Chromium"
date: 2016-12-13
forum: Desktop Environments
---

### Post by philhughes on 2016-12-13
I cannot access amazon.co.uk or amazon.com with Chromium browser, but it works fine with Firefox. With Chromium I get "Your connection is not private" ... blah blah ... NET::ERR_CERTIFICATE_TRANSPARENCY_REQUIRED.

The Amazon certificate is issued by Symantec. In Firefox, I can see Symantec certificates (under the Verisign authority), but none are listed under Chromium. Not sure exactly when this behaviour started (I mainly use Firefox), but it was in the last few days. Happens on 2 fully up to date PCs running Ubuntu 16.10.

Anyone else seeing this? Any possible solutions? Thanks

Edit: I have exported the "Symantec Class 3 Secure Server CA - G4" certificate from Firefox and imported it into Chromium, and I can now access amazon from Chromium. For some reason it seems Chromium is not seeing / does not have the Symantec certificates.

---

### Post by howefield on 2016-12-13
Have a browse at this thread : [https://ubuntuforums.org/showthread.php?t=2343655](https://ubuntuforums.org/showthread.php?t=2343655)

---

### Post by philhughes on 2016-12-13
Thanks Howefield. I did a search for amazon here and on askubuntu, but nothing came up. Amazon was the only site I'd seen this on, didn't realize it was a wider problem. I assume exporting the cert from Firefox is an acceptable workaround until it gets updated if anyone must use Chromium.

---

