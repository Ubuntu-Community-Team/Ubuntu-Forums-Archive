---
title: "Application throttling"
date: 2008-12-09
forum: General Help
---

### Post by Neovos on 2008-12-09
I'm curious if anyone is aware of a way to (or a program for) throttling specific programs or processes so that they don't eat up certain amounts of CPU. I have some thrown together rigs that are very sensitive to temperature and would like to be able to put a ceiling on the amount of CPU some certain programs use. I know that programs like boinc can throttle by actually pausing and starting the computation in a certain frequency directly related to the % of CPU I tell it to run. But if done by a third party program, this may cause the program to "jitter." So if not that, then some type of percentage ceiling perhaps? Is there a hack for this or a program someone knows about?

---

### Post by dcstar on 2008-12-10
> **Neovos said:**
> I'm curious if anyone is aware of a way to (or a program for) throttling specific programs or processes so that they don't eat up certain amounts of CPU. I have some thrown together rigs that are very sensitive to temperature and would like to be able to put a ceiling on the amount of CPU some certain programs use. I know that programs like boinc can throttle by actually pausing and starting the computation in a certain frequency directly related to the % of CPU I tell it to run. But if done by a third party program, this may cause the program to "jitter." So if not that, then some type of percentage ceiling perhaps? Is there a hack for this or a program someone knows about?

```
man nice
```

---

### Post by Neovos on 2008-12-10
thanks for the suggestion but nice values just affect priority but still allow a program to run at 100% cpu if it wants to. What I'm looking to do is not allow a program to ever use any more then say 40% of the cpu at any one time. It's irrelevant whether its a low priority or high priority task, I'm looking for a program specific CPU percentage cap.

---

