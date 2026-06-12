---
title: "i cant get skydome to work on compiz...help please"
date: 2009-03-30
forum: General Help
---

### Post by xpinsx on 2009-03-30
i got the cube to work, and everything else to work besides the write in fire and skydome

---

### Post by spiderbatdad on 2009-03-30
You have checked the skydome box and selected a file from the appearance tab under cube settings, as shown in the screenshot below?

---

### Post by xpinsx on 2009-03-30
my ccsm doesnt look anything like that......

---

### Post by phantom3113 on 2009-03-30
What version of Ubuntu are you running and have you installed the package compizconfig settings manager?

Do you have the compiz fusion extra plugins package?

---

### Post by xpinsx on 2009-03-30
im running ubuntu 8.10. as far as i know, ive installed the compizconfig settings manager

im not sure if i have the extra plugins package....how would i check/get it?



and sorry if these are noobish questions....i just installed ubuntu yesterday

---

### Post by phantom3113 on 2009-03-30
Under the Package Manager (System>>Administration>>Synaptic Package Manager) search for compiz-fusion-plugins-extra and mark it for install, or run:

```
sudo apt-get install compiz-fusion-plugins-extra
```

to install it from the terminal. Also, could you post a screenshot of what your ccsm looks like?

Don't worry, everyone has to be a noob at some point :P

---

### Post by xpinsx on 2009-03-30
yeah, ill post a screenshot. give me a sec. and there were a couple of packages that werent installed, and i installed them



just kidding i found it

---

### Post by phantom3113 on 2009-03-30
Ah, so it was hiding! :D Glad you found it, although you may find some pictures don't show up with the skydome. I'm not sure why it does that, but I think skydome may just be picky :P

---

### Post by xpinsx on 2009-03-30
ok. here's the screenshot

a bit messy lol. it looks alot different than other peoples ccsm;s, ive noticed

---

### Post by phantom3113 on 2009-03-30
Ah, ok. From there skydome should be under desktop cube on the "appearance" tab. Of course, if you found it I guess you know that :)

---

### Post by xpinsx on 2009-03-30
whenever i click on "desktop cube", it just takes away all the icons from everything and doesnt do anything......so i dont really think i have an appearance tab. its weird

---

### Post by phantom3113 on 2009-03-30
hm...odd. Ok, it sounds as though you might be missing some packages or something, so try this. Go into the package manager again and search for compizconfig-settings-manager; fusion-icon; and emerald. If any of them are already marked as installed, mark them for re-install. Also, which graphics card are you using? lspci tells you

---

### Post by xpinsx on 2009-03-31
oh lawdy!!!! i got it! thank you so much!


sudo buy phantom3113 a pony

---

### Post by phantom3113 on 2009-03-31
:D I'm glad you got it! And thanks for the pony too! :P

---

### Post by xpinsx on 2009-03-31
one more question......how do i get the windows to like turn into fire when i open and close them?

---

