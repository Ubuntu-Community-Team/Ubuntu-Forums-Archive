---
title: "Why is my system using swap"
date: 2009-01-14
forum: General Help
---

### Post by sn0m on 2009-01-14
I'm not sure why my system is using swap where there's plenty of RAM.
Attached is screen-shot from htop.
Regards
Sokol

---

### Post by hangfire on 2009-01-14
> **sn0m said:**
> I'm not sure why my system is using swap where there's plenty of RAM.
Attached is screen-shot from htop.
Regards
Sokol

You are running a lot of instances of Rhythmbox. Do you need more than one?

-HF

---

### Post by sn0m on 2009-01-14
Mmm, good point, I only use it to listen to internet radio and according to me it is only one rhythmbox running, not 5, so not sure, however I thought the system will use swap once it has run out of RAM? Am I wrong?
Sokol

---

### Post by mc4man on 2009-01-14
> however I thought the system will use swap once it has run out of RAM? Am I wrong?

It doesn't really work like that. There are ton's of pages on how swap works in linux and whether it's needed with large ram, ect. If you do some google searches you can find as much as you want to know.

---

### Post by redilyn on 2009-01-14
After you finish researching the subject you may decide you do not want to use swap as often. If that is the case try the following

```

sudo gedit /etc/sysctl.conf

```

add the following

```

vm.swappiness=5  <-- The lower the number the less swap is used

```

Then run

```

sudo sysctl -p

```

Cheers

---

