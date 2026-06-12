---
title: "Unity vs lowlatency kernel?"
date: 2014-04-23
forum: Desktop Environments
---

### Post by dewdrop_world on 2014-04-23
I'm setting up a new system after my 3.5-year-old laptop died -- Ubuntu 12.04*, now on a ThinkPad E431. It's running beautifully, except for one thing.

I do a lot of real-time audio work in SuperCollider, and this benefits from the lowlatency kernel. Every time I log into Unity after booting the low latency kernel, it runs unity_support_test, and this crashes, producing apport dialog boxes that I have to dismiss. Everything else seems to be working fine (though today is the first time I tried to use the low latency kernel on this machine, and that's been for just 10 minutes or so -- still, I don't see any untoward behavior).

This happens with both Unity 3D and 2D. (Currently I'm running Unity 2D, because I don't need the crazy graphics effects stealing CPU cycles from signal processing.) On my old machine, I used Gnome with the low latency kernel, absolutely no problems.

Should I be concerned about this?

```
Linux hjh-e431 3.2.0-60-lowlatency #62-Ubuntu SMP PREEMPT Tue Feb 25 00:11:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Thanks,
hjh

* I'll upgrade to 14.04 sometime later this year, but for now, I need the system to be stable so I'm going with the older version.

---

### Post by sudodus on 2014-04-24
Do you know ***Ubuntu Studio***? It is a community flavour of Ubuntu, that is made for your kind of applications. See this link

[http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by dewdrop_world on 2014-04-24
> **sudodus said:**
> Do you know ***Ubuntu Studio***? It is a community flavour of Ubuntu, that is made for your kind of applications. See this link

[http://ubuntustudio.org/](http://ubuntustudio.org/)

I do know ubuntustudio, and I might try it when I go up to 14.04 later this year. For now, I'm not in a position to introduce any new points of failure in a system that's basically working perfectly (except I haven't dealt with rtirq yet... weekend task).

Thanks though.

hjh

---

### Post by dewdrop_world on 2014-04-26
Hm, actually, I just had to go back to the generic kernel temporarily, for another reason. And I still got the crash from unity_support_test.

So it isn't only the low latency kernel.

Otherwise, the system is stable, so I'm not especially worried about it. But it's untidy.

hjh

---

