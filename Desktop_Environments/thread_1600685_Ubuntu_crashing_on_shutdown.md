---
title: "Ubuntu crashing on shutdown"
date: 2010-10-19
forum: Desktop Environments
---

### Post by paulsp on 2010-10-19
I had this problem in 10.04 and hoped it would go away in 10.10, but it did not. My computer crashes on shutdown. When the system is shutting down, the screen goes black (sometimes with a bunch of grey lines), and just hangs. I have waited for a long time but nothing happens. I have to shut it down manually, with file losses as a result. How should I go about fixing this? I have looked a bit in /var/log but do not know where to look for. Where can I find what is causing this?

---

### Post by mister_p_1998 on 2010-10-20
is it running on old hardware? putting ACPI=force into the grub menu on the kernal line fixed it for me on an old AMD.
Steve

---

### Post by paulsp on 2010-10-20
Thanks for your reply! It's a P4 2.8 GHZ system, not very old. And it worked well before, it's just all of a sudden that it crashes. Could this still work you think?

---

### Post by searchfgold6789 on 2010-10-20
I also vote for the suggestion of putting "acpi=force" on the kernel line options; lots of guides online for that.
I was having the same problem. I tried that and didn't see immediate results but after awhile my computer was shutting down and restarting normally again.
Downgrading from Grub 2 to Grub Legacy will probably fix it. Grub 2 is only a testing version and ships with Ubuntu anyway for some reason. But not many people are willing to do that.

---

