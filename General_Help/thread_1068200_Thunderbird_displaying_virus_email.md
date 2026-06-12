---
title: "Thunderbird displaying virus email?"
date: 2009-02-12
forum: General Help
---

### Post by Rage10898 on 2009-02-12
I am currently using Thunderbird 2.0.0.19 on Intrepid and every email I download and try and read, comes up saying that it has been received from PayPal Australia and then displays an email from PayPal.

This doesn't matter if it is an email from a company - Ubisoft, US Cav, whoever, or from a private email account - I have sent myself test messages and they come up the same as well.:confused:

If I were using Windows, I'd say it was viral, but this is Ubuntu...

Anybody have any ideas?  I have searched the forums, but having no luck.

Thanks.

---

### Post by ajmorris on 2009-02-13
> **Rage10898 said:**
> I am currently using Thunderbird 2.0.0.19 on Intrepid and every email I download and try and read, comes up saying that it has been received from PayPal Australia and then displays an email from PayPal.

This doesn't matter if it is an email from a company - Ubisoft, US Cav, whoever, or from a private email account - I have sent myself test messages and they come up the same as well.:confused:

If I were using Windows, I'd say it was viral, but this is Ubuntu...

Anybody have any ideas?  I have searched the forums, but having no luck.

Thanks.

hi there,
Try doing the following:
```
mv ~/.thunderbird ~/.thunderbird.backup
```
This will move your whole thunderbird profile.
Then startup thunderbird, and re-add your email account, download your emails, and try viewing them to see if the issue is rectified.

AJ

---

