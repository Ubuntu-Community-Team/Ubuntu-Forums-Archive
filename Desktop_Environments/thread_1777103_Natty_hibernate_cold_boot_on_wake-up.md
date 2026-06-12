---
title: "Natty hibernate: cold boot on wake-up"
date: 2011-06-07
forum: Desktop Environments
---

### Post by frankvw on 2011-06-07
Hi, everyone,

There's one other annoyance with my new Natty install on my HP-550 laptop: hibernation doesn't work. When I select 'hibernate' in the shutdown menu there is some activity that looks like it's going into hibernation, i.e. there's no normal shutdown procedure... but when I then switch the system back on it just boots into a new session, i.e. from scratch as if it never went into hibernation.

What can I do to figure out what's going on here? Suggestions, anyone?

Thanks - all replies appreciated!

// FvW

---

### Post by frogotronic on 2011-06-28
Same behaviour here.

Looks as if its being dropped: [http://www.mail-archive.com/ubuntu-devel@lists.ubuntu.com/msg00581.html](http://www.mail-archive.com/ubuntu-devel@lists.ubuntu.com/msg00581.html)

---

### Post by mcduck on 2011-06-28
> **frankvw said:**
> Hi, everyone,

There's one other annoyance with my new Natty install on my HP-550 laptop: hibernation doesn't work. When I select 'hibernate' in the shutdown menu there is some activity that looks like it's going into hibernation, i.e. there's no normal shutdown procedure... but when I then switch the system back on it just boots into a new session, i.e. from scratch as if it never went into hibernation.

What can I do to figure out what's going on here? Suggestions, anyone?

Thanks - all replies appreciated!

// FvW

How much you have RAM and swap space on the system?

You need a working swap partition that's at least equal to the amount of RAM in use at the moment to successfully hibernate.

Run "free -m" in a terminal to check the amount of RAM and detected swap.

---

### Post by dFlyer on 2011-06-28
Sometime hibernate looks like a reboot but it isn't. Have you tried leaving a few programs open when you hibernate so when you restart they should still be open, if they are not then you will know for sure that the system shutdown and didn't hibernate.

---

### Post by frankvw on 2011-06-29
> **cement_head said:**
> Same behaviour here.

Looks as if its being dropped: [http://www.mail-archive.com/ubuntu-devel@lists.ubuntu.com/msg00581.html](http://www.mail-archive.com/ubuntu-devel@lists.ubuntu.com/msg00581.html)

Yes, I had seen that thread before. And frankly it makes no sense to me. How can you drop support for hibernation? It's a feature used regularly by many. I don't understand.

Anyway, still looking for a solution. Suspend is a little bit of a work-around, but not an option if, say, you have to change batteries in mid-flight (as I have had to do a couple of times already).

---

### Post by frankvw on 2011-06-29
> **mcduck said:**
> How much you have RAM and swap space on the system?

You need a working swap partition that's at least equal to the amount of RAM in use at the moment to successfully hibernate.

Run "free -m" in a terminal to check the amount of RAM and detected swap.

Output:
```

             total       used       free     shared    buffers     cached
Mem:          3014       2982         32          0        695        513
-/+ buffers/cache:       1773       1241
Swap:         6675          0       6675

```

When I ran 8.04 on the same laptop in more or less the same configuration (running pretty much the same apps, too) I never had any memory problems.

So that's not it. But even if it was, I'd expect to see an error message or at least a warning about it, instead of it just failing without any complaints to suggest what's happening. I mean, we're not talking Windoze here, right? :-)

---

### Post by frankvw on 2011-06-29
> **dFlyer said:**
> Sometime hibernate looks like a reboot but it isn't.Trust me. I've been working in the nuts-and-bolts side of IT for about 20 years now. I think I may safely state that I know a reboot when I see one. :-)

> **dFlyer said:**
> Have you tried leaving a few programs open when you hibernate so when you restart they should still be open, if they are not then you will know for sure that the system shutdown and didn't hibernate.Of course I have done that. That's what hibernation is for, isn't it? And how else would I have determined that what I'm getting is a cold boot rather than a wake-up from hibernation?

---

### Post by federico_hyo on 2011-08-08
I have same problem here, whenever I use the hibernate function the laptop seems to hibernate correctly.. ie. hard drive light switch on and then it really looks ok. But when I switch it on by pressing the power button a new session start from scratch. I have same amount of swap as ram.
I'm using ubuntu natty 11.04 on a sony vaio x laptop.

any solution .. so far?

---

