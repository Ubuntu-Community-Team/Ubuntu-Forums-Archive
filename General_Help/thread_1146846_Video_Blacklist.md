---
title: "Video Blacklist"
date: 2009-05-03
forum: General Help
---

### Post by theozzlives on 2009-05-03
I've been trying to take my Intel video out of my blacklist. In Jaunty /etc/modprobe.d/blacklist doesn't exist, instead there's a few files none of which have my video in it. Where'd Jaunty put the video blacklist?

---

### Post by BslBryan on 2009-05-03
Yeah, it does. :)

```
sudo gedit /etc/modprobe.d/blacklist
```

---

### Post by Psychopump on 2009-05-09
> **BslBryan said:**
> Yeah, it does. :)

```
sudo gedit /etc/modprobe.d/blacklist
```

er....no it doesn't.

---

### Post by Yellow Pasque on 2009-05-09
If you mean the Compiz blacklist, run this:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```
If you have problems with video playback and Compiz, don't report it on Launchpad. The developers won't want to hear about them (until appropriate upstream fixes are in place).

---

### Post by theozzlives on 2009-05-09
> Rhetorical question: What would happen if your hard disk physically failed right now?

My data's on my server so I guess I'd have to buy a new drive. Yes I did mean compiz, but I thought it looked to the Ubuntu Blacklist.

---

### Post by Yellow Pasque on 2009-05-09
No, the kernel module blacklist and compiz blacklist are separate entities. Did the command help or not?

---

### Post by theozzlives on 2009-05-09
> **Temüjin said:**
> No, the kernel module blacklist and compiz blacklist are separate entities. Did the command help or not?

yeah, thanks

---

