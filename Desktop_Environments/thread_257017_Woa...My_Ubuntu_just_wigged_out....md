---
title: "Woa...My Ubuntu just wigged out..."
date: 2006-09-13
forum: Desktop Environments
---

### Post by Burgresso on 2006-09-13
I was using my computer when the screen went black, then the bottom half went like static and white line appeared at the top. Went black again, then I got kicked out of Gnome, and the Nvidia logo appeared, and the Gnome login screen came up again.

What happened and what does this mean? What should I do?

---

### Post by BoneKracker on 2006-09-14
Dude, sounds like X reinitialized it's gnarly self.

I'd like, blow it right off unless it happens like, repeatedly.

Or, you could eyeball your /var/log/Xorg.0.log file and see if you can cognify what the deal is.

---

### Post by nrwilk on 2006-09-14
Could you have accidentally hit ctrl-alt-backspace?

That would restart your x-server, doing exactly what you're describing.

---

### Post by BoneKracker on 2006-09-14
the other thing that comes to mind is a loose graphics card

unless you were doing something video-settings-related just before it happened

---

### Post by Burgresso on 2006-09-14
Thanks for the responses. :)

It is concievable that I pressed ctrl-alt-backspace. I have an integrated video card.

I won't let it bother me - I just it does not happen again. I'll take a look my xorg file, too, but I'm too sure what to look for.

Thanks again,

burgresso

---

### Post by BoneKracker on 2006-09-15
If it happens again...

```
grep "EE" < /var/log/Xorg.0.log
```
and also for "WW"


In case X actually restarted, you may also want to have a look at Xorg.0.log.old

The errors and/or warnings might give you some indication of what went wrong.

---

