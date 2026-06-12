---
title: "printer gets blocked after every use"
date: 2006-09-12
forum: Desktop Environments
---

### Post by ivantxu on 2006-09-12
Hi there everyone.

I've been having some problems with an HP LaserJet 1300 sitting in a USB port.  The printer got detected and was configured fine, and indeed it works fine if I send a printer job to the queue, but after a first job it just gets blocked.  Cups' error_log shows this message

```
cupsdAuthorize: Local authentication certificate not found
```

If I switch off and then on the printer and send the print job again, it works fine but again only for one job.

Any ideas? TIA

Ivan

---

### Post by Confuse on 2006-09-26
I can confirm this behavior, but I get no output from the cups logs. I'm also using turboprint and the latest cups stable with dapper.

---

