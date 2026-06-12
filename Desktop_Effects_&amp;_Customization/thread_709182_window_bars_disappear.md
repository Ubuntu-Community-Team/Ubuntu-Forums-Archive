---
title: "window bars disappear"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by boddhisatva on 2008-02-27
Hi
I know similar problems have been raised, but I didn't find a working answer in the forums. When I try to turn on desktop effects, even the default "normal" mode, window bars disappear. The annoying thing is, when I first installed Ubuntu it did work, including the advanced effects. Then, after some time,  they disappeared. I thought it was because I had installed, and then removed, Kubuntu environment (I thought I had removed too many files which I thought Kubuntu had left behind). However, upon a second installation of Ubuntu (after a hard disk format and all) the effects worked OK only when I first started the system. After the second reboot they disappeared again, and I haven't been able to get the window bars ever since, although I have  tried a few things. Any help?

---

### Post by swatto on 2008-02-27
Hi,

What window-decorator are you using? if it's emerald type this in a terminal:

```
emerald --replace & disown
```

that should do the trick I think. :)

---

### Post by boddhisatva on 2008-02-27
Thanks for the response. swatto.
I'm afraid that doesn't help, though. :(

---

### Post by Therion on 2008-02-27
Whoops... Massive edit underway.  Stay tuned.

---

### Post by Promaster91 on 2008-02-27
Are you using compiz???

```

compiz --replace

```

---

### Post by kdm on 2008-06-16
> **swatto said:**
> Hi,

What window-decorator are you using? if it's emerald type this in a terminal:

```
emerald --replace & disown
```

that should do the trick I think. :)

This worked a treat - Thanks !

---

