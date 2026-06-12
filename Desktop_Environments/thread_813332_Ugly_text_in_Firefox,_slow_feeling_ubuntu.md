---
title: "Ugly text in Firefox, slow feeling ubuntu"
date: 2008-05-30
forum: Desktop Environments
---

### Post by bla on 2008-05-30
Hey there,

I'm new to ubuntu and would like to know:

(1) what font I shoud use/install to get rid of the ugly font in firefox?
I find the text unbarable in ubuntu. In XP, using firefox, the text is clean and readable. With ubuntu i find the text on the net to be very bad. It is OK on the desktop.

(2) I find ubuntu 8.04 (I have used no other version) somewhat slow compared to XP.  XP is extremely fast.  Ubuntu feels slow and heavy.
Are there tweaks to speed up ubuntu?

I have a core2duo t7500 and NVIDIA 8600.
Nvidia driver via envy.
Newest kernel...

Why is this and how can I fix it?

---

### Post by Bakon Jarser on 2008-05-30
Go to the terminal

Applications > Accessories > Terminal

and enter this

```
sudo apt-get install msttcorefonts
```

should solve your font problem.

---

### Post by vvvjr on 2008-05-31
Even after this my firefox fonts still baaad. so I picked settings from my xp box. no luck.  what am I doing wrong.

> **Bakon Jarser said:**
> Go to the terminal

Applications > Accessories > Terminal

and enter this

```
sudo apt-get install msttcorefonts
```

should solve your font problem.

---

### Post by jejones3141 on 2008-05-31
What kind of display do you have? If it's an LCD, you'll want to make sure that subpixel rendering is turned on, if you haven't already done so.

---

### Post by Blasphemer on 2008-05-31
> **jejones3141 said:**
> What kind of display do you have? If it's an LCD, you'll want to make sure that subpixel rendering is turned on, if you haven't already done so.
How do you switch on subpixle rendering?

---

### Post by benerivo on 2008-05-31
Main Menu > System > Preferneces > Appearance.
In the window, choose the 'Fonts' tab and click the 'details' button.

---

### Post by bla on 2008-06-01
thanks, seems to have installed some fonts.  Now, i'll have to match up the fonts selected in both firefoxes.

---

