---
title: "Minimizing Evolution to Panel - How?"
date: 2007-05-05
forum: Desktop Environments
---

### Post by Left hand of Gaia on 2007-05-05
Morning all,

I have evolution setup, but I'm trying to find out if there are plugins to minimize it to the gnome-panel, similar to Gaim.  

Can anyone point me to an answer?

Regards

---

### Post by gaspar on 2007-05-05
I´m not sure if Evolution has this option (I think it does not).
Had you tried [alltray]("http://packages.ubuntu.com/feisty/x11/alltray")?

---

### Post by Left hand of Gaia on 2007-05-05
gaspar: Thanks, alltray solves my problem, exactly as I wanted it to.

Regards,

Left Hand of Gaia

---

### Post by heimo on 2007-05-06
Thanks gaspar, it's a nice little program! To launch evolution, I have an application launcher on top panel. I installed alltray:
```
sudo aptitude install alltray
```

And changed application launcher to:
> alltray evolution --component=mail

And now clicking close window on evolution will minimize it to tray. Cool. :)

---

### Post by tyler22 on 2007-05-08
I installed alltray,

I run it and click on evolution or any other window and it does nothing :S

I followed the simple instructions it gives on screen, am i missing something?

---

### Post by tyler22 on 2007-05-10
anyone?

---

### Post by tonywhelan on 2007-05-22
As indicated above, you DO NOT launch Evolution directly. 

You change the launcher properties of the icon or menu item to read:
alltray evolution --component=mail

---

### Post by borobudur on 2007-05-26
Is it possible that alltray doesn't exist for amd64 architecture?

---

### Post by tonywhelan on 2007-05-26
I am using alltray on an AMD 64 bit machine  under Edgy

---

### Post by FlashDude on 2007-06-13
It works for me.  I installed alltray from synaptic and right clicked the shortcut and clicked properties and in the command line take out whats there and put the code that is listed above in there and it works perfectly.

---

### Post by Raval on 2008-01-28
> **heimo said:**
> Thanks gaspar, it's a nice little program! To launch evolution, I have an application launcher on top panel. I installed alltray:
```
sudo aptitude install alltray
```And changed application launcher to:


And now clicking close window on evolution will minimize it to tray. Cool. :)

thanks this worked for me, dunno why they don't add this feature to evolution.

---

