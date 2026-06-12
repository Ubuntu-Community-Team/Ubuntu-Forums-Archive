---
title: "Question about typing issue on Ubuntu and Wayland vs X.org"
date: 2021-09-20
forum: Desktop Environments
---

### Post by tomdkat on 2021-09-20
Hi!  Today, I experienced something truly bizarre:  after entering my login password, anything I typed refused to appear anywhere!  First, I had problems typing a URL in Firefox, then when I opened a terminal window and typed, nothing appeared.  The caps lock and num lock keys caused the corresponding lights to work on the keyboard but nothing would appear on the screen and the cursor didn't move.  This was after a couple of reboots too.  Then, I rebooted and chose "Ubuntu on X.org" instead of "Ubuntu", as a login option, and the typing issue went away.   

Here is my system info:

```
tom@deathstar:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 21.04
Release:	21.04
Codename:	hirsute
tom@deathstar:~$ uname -a
Linux deathstar 5.11.0-34-generic #36-Ubuntu SMP Thu Aug 26 19:22:09 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
tom@deathstar:~$ 

```

Any ideas on what the issue could be?  I will continue using "Ubuntu on X.org", for the time being.

Thanks in advance!

Peace...

---

### Post by monkeybrain20122 on 2021-09-21
It is a wayland issue. Just stick with xorg now. I see the same on archlinux.

---

### Post by kurt18947 on 2021-09-22
Interesting. I've been using Wayland exclusively on 20.04 with no problem. I guess there's something in 21.04 that Wayland doesn't like.

---

### Post by tomdkat on 2021-09-25
> **monkeybrain20122 said:**
> It is a wayland issue. Just stick with xorg now. I see the same on archlinux.

Thanks!

Peace...

---

### Post by tomdkat on 2021-09-25
> **kurt18947 said:**
> Interesting. I've been using Wayland exclusively on 20.04 with no problem. I guess there's something in 21.04 that Wayland doesn't like.It's weird because Wayland was working fine, on 21.04, up until I started this thread.  So, something changed and I don't know what.   I'm running GNOME on Xorg and it's working well. :)

Peace...

---

