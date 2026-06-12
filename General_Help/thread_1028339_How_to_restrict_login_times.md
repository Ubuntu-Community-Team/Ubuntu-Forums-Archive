---
title: "How to restrict login times?"
date: 2009-01-02
forum: General Help
---

### Post by rocketman768 on 2009-01-02
Is there a way to restrict the days and times that a user is allowed to be logged in? I need this for my kid sister.

---

### Post by ibutho on 2009-01-02
Hi. You probably need to look at a pam module called pam_time. Unfortunately its not something I have used so can't give you specific details on how to use it.

---

### Post by ushimitsudoki on 2009-01-02
[pam_time - time controled access]("http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_time.html")
> The pam_time PAM module does not authenticate the user, but instead it restricts access to a system and or specific applications at various times of the day and on specific days or over various terminal lines. This module can be configured to deny access to (individual) users based on their name, the time of day, the day of week, the service they are applying for and their terminal from which they are making their request. 

---

### Post by rocketman768 on 2009-01-02
Thanks to both of you. It at least lets me restrict when she logs in. But, unfortunately doesn't force her to log out...

> Note, currently there is no daemon enforcing the end of a session. This needs to be remedied. 

---

### Post by spiderbatdad on 2009-01-02
timekpr

[http://linux.softpedia.com/progScreenshots/Timekpr-Screenshot-42110.html](http://linux.softpedia.com/progScreenshots/Timekpr-Screenshot-42110.html)

[https://launchpad.net/timekpr](https://launchpad.net/timekpr)

deb package here: [http://savvas.radevic.com/timekpr/](http://savvas.radevic.com/timekpr/)

---

