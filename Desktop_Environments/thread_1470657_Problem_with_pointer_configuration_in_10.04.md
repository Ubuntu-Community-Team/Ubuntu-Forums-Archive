---
title: "Problem with pointer configuration in 10.04"
date: 2010-05-03
forum: Desktop Environments
---

### Post by rozen on 2010-05-03
Hi,

I did an upgrade from 9.10 to 10.04 and it mostly went well.  It was a fairly extensive upgrade with the KDE desktop and involved downloading 2100 files that took many hours.

I did not like the new theme and background so I changed to "human" theme and am now fighting with occasional missing window borders.

My biggest problem is that I customized the pointer to be  "redglass" and made it as large as possible.  When over some windows like Firefox and Emacs, I get the big red arrow that I want. However, over most other windows like synaptic and gnucash as well as the background, I have a tiny little arrow which I can barely see.

I also did a new installation on another partition and the pointer seems to be what I want.  I would really like to stay with my updated version because I have so much stuff there and don't really want to go and install and configure everything again. It would tak weeks!

I would really appreciate any suggestion that will lead me to a large pointer everywhere.

Many Thanks in Advance,
Don

---

### Post by bshkv on 2010-05-03
what abot video card and driver?
compiz is rnning?
And engine for your window decoration theme is instaled?
I have the same problem and in root accont everything work fine, not in other account but have time to solve:)

---

### Post by rozen on 2010-05-03
My machine has an nvidia GForce 7300LE and I am using the nvidia driver, also I am running compiz.

I don't know what you mean by "engine for your window decoration theme is installed?" so I don't know.

But I just discovered that if I set visual effects to "None", the cursor will work fine.

---

### Post by stinkeye on 2010-05-03
Try making icons and themes stored in your home folder available to root.```
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.themes /root/.themes
```

---

### Post by rozen on 2010-05-03
I tried your suggestion of linking icons and themes to /root and logged out and logged back in but still had the problem.

---

