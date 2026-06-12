---
title: "How to start GUI after login on command line?"
date: 2009-04-20
forum: General Help
---

### Post by schoi.mosaic on 2009-04-20
As a biginner of ubuntu 8.10, here is my question. How do I start GUI after login on command line?

The problem I have now is this:
I changed login window from default to new one.Then, whenever I boot, the new login window comes out and keeps running without further progress.

So, what I am trying to do is that I am going to login on command line first, and start my GNOME, but I am a absolute beginner of linux commands.

I appreciate it if anybody can help me.

Thanks.

---

### Post by killerdogg77 on 2009-04-20
Try
```
sudo /etc/init.d/gdm start
```

---

### Post by celthunder on 2009-04-20
ctrl+alt+f2 (get to a terminal) log in from there and type startx to get into gnome (assuming gnome is your default de)

---

### Post by schoi.mosaic on 2009-04-20
Thank you killerdogg77 and celthunder.

I tried gdm start and it showed login window. Then I could go into my GNOME desktop.

Yes, my default is GNOME, and I guess startx is the command I can generally use whenever I have GUI trouble..

Thanks again.

---

