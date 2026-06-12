---
title: "Apps all start up full-screen on Mini 10"
date: 2009-08-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fjgaude on 2009-08-28
Is there a way to stop the apps from going full-screen on start-up on the Mini 10 running factory installed Ubuntu 8.04?

Thanks!

---

### Post by nwadams on 2009-08-28
your mini 10 must come with the netbook remix installed. that is one of the features by default. umm. if you look in the preferences is there a way to switch back to the default ubuntu desktop?

---

### Post by fjgaude on 2009-08-28
Thanks for your reply... but I'm using the normal, default Ubuntu desktop, not the one with the boxes.

I've looked over the Configuration Editor but didn't see anything that could permit full-screen window support at app start. It's not a big deal as you can click the Unmaximize square in the upper right corner of the app window. I guess because I have the 1333 x 768 screen resolution it becomes an issue. The normal screen is 1024 x 768 and that might be the way most folks like it.

---

### Post by Greyed on 2009-08-29
```

sudo chmod 000 /usr/sbin/maximus

```I just went through that myself with my mini 10v.  The application which is auto-resizing is called Maximus.  Unfortunately it is a depends on other UNR packages which might be good to have.  So the simplest way to tell it to shove off is just to prevent it from running.  You'll also need to locate the current running Maximus and kill it.

From what I can figure out there is no configuration for it.  :(

---

### Post by fjgaude on 2009-08-29
Thanks, that does it. Wow, who would have thunk it! The actual file is in /usr/bin not /sbin.

---

### Post by karamu on 2009-09-02
I resolved the same issue by removing the maximus package but then I installed regular Ubuntu (Jaunty then Karmic) and never went back to Dellbuntu/ UNR......

---

### Post by fjgaude on 2009-09-02
Well, I have 9.04 on a LiveUSB flash drive. It boots my mini 10 fine except for my 1333 x768 screen resolution... I end up with 1024 x 768, not good. I await to see what 9.10 is like.

I have no issue with Maximus... gone, as stated earlier!

Do you know if I could change something in X11.org to handle the 1333 screen?

---

