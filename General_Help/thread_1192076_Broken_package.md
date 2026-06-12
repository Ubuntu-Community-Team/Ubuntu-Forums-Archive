---
title: "Broken package"
date: 2009-06-19
forum: General Help
---

### Post by Bigtime_Scrub on 2009-06-19
I got an update icon notification. Nothing unusual and so I click on it to download and install the updates. I get an error that not all updates installed. I get this from the update:

```
E: /var/cache/apt/archives/tzdata_2009j-0ubuntu0.9.04_all.deb: subprocess rm cleanup killed by signal (Killed)
```

I have never had an error that an update package failed and could not install. I've tried again 3 more times and it fails each time.

---

### Post by dcstar on 2009-06-20
> **Bigtime_Scrub said:**
> I got an update icon notification. Nothing unusual and so I click on it to download and install the updates. I get an error that not all updates installed. I get this from the update:

```
E: /var/cache/apt/archives/tzdata_2009j-0ubuntu0.9.04_all.deb: subprocess rm cleanup killed by signal (Killed)
```

I have never had an error that an update package failed and could not install. I've tried again 3 more times and it fails each time.

Delete that file, it is probably corrupted.

---

