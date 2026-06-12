---
title: "nextcloud client certificate issue"
date: 2020-11-01
forum: Desktop Environments
---

### Post by lister171254 on 2020-11-01
I've posted this in the nextcloud forum too, but still have not found a solution.
I'm running the latest LTS Desktop version of Ubuntu with nextcloud desktop version 2.6.2-1build1.

When trying to login into on of my Nextcloud servers I get the attached error.

When I use the browser to login to the same site, the certificate is fine (see second attachment).

Thanks,

Leo

---

### Post by TheFu on 2020-11-02
I didn't see the same problems.  If you visit the nextcloud webapp directly through a browser, are there any cert errors? If so, those will need to be fixed.  The errors show 2 different certs and FQDN. Looks like you have the wrong URL or the cert was created with the nextcloud domain missing.

I setup the nextcloud-desktop program 9same version as you have) on a 20.04.1 system here. Didn't see any errors ... well ... except the normal Gnome crap errors for GIO not working. Those are all expected. No cert issues at all.

---

### Post by lister171254 on 2020-11-02
Not sure what you mean by "The errors show 2 different certs and FQDN"

The screenshot shows that the cert is for *.dragonclaw.net and that it's valid until Jan 2021. 
The question is why the client cannot verify the cert for nextcloud.dragonclaw.net

---

### Post by TheFu on 2020-11-02
The cert common name is zudiewiener.com, not dragonclaw.net. That's the failure.

---

### Post by lister171254 on 2020-11-02
Dogghhh,

I provided the wrong sreenshot.
Attached is the correct cert via the browser.

---

### Post by TheFu on 2020-11-03
Sorry, I don't use wildcard certs.

---

