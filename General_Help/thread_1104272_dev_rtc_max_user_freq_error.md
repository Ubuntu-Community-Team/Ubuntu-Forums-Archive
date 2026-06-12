---
title: "dev rtc max user freq error"
date: 2009-03-23
forum: General Help
---

### Post by RonPDX on 2009-03-23
Afternoon everyone, 

While booting I notice that I receiving the following error:

```

error:

dev.rtc.max-user-freq is an unknown key

etc/sysct1.conf

```

After taking a look a the sysct1.conf file the max-user-freq is set to 1026. 

Can anyone point me in the direction to correct this error?

---

### Post by dcstar on 2009-03-24
> **RonPDX said:**
> Afternoon everyone, 

While booting I notice that I receiving the following error:

```

error:

dev.rtc.max-user-freq is an unknown key

etc/sysct1.conf

```

After taking a look a the sysct1.conf file the max-user-freq is set to 1026. 

Can anyone point me in the direction to correct this error?

```
sudo sysctl -a
``` will show you all valid keys.

---

### Post by RonPDX on 2009-03-24
David -- Thanks for your response, I have looked the results that you suggested and dev.rtc.max-user-freq is not listed. Would it be safe to either delete it or keep in the config file as a # note?

---

