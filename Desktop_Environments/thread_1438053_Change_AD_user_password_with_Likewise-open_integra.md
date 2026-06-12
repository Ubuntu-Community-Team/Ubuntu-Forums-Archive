---
title: "Change AD user password with Likewise-open integration"
date: 2010-03-24
forum: Desktop Environments
---

### Post by claytronic on 2010-03-24
I'm posting this to help other Ubuntu users that are joining their machines to an Active Directory network and need to change their user account password.

If you use the standard *passwd* command you'll get an unhelpful error.

```
$ passwd
Current password:
New password:
Re-enter password:
Password does not meet requirements
passwd: Authentication token manipulation error
passwd: password unchanged

```

You will need to use the ***kpasswd*** command instead.

---

### Post by claytronic on 2010-03-25
Update:

My previous post was incorrect. What I didn't realize was that the Active Directory domain's security policy only allowed one password change during a 24 hour period. It was just by coincidence that my usage of *kpasswd* occurred a few moments after 1 day of my previous change. 

This morning I temporarily lowered the AD security policy for testing.

Using Group Policy Manager Editor (GPME)
Default Domain > Computer Configuration > Policies > Security Settings > Account Policies > Password Policy > Minimum password age = 0 days

**Note**: I do not recommend leaving the policy set to zero days. That could allow a rogue entity to change passwords without the true user noticing 

Next I cleared the Likewise-open cache:

```
sudo service lsassd stop
sudo rm -f /var/lib/likewise/db/lsass-adcache.db
sudo rm -f /var/lib/likewise/db/lsass-local.db
sudo service lsassd start
```

Then I was able to change password from either *passwd* or *kpasswd* as many times as I wanted as long as they were different and met the complexity requirements.

---

