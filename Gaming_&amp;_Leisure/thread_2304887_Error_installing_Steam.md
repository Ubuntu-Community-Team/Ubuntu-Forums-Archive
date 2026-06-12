---
title: "Error installing Steam"
date: 2015-11-30
forum: Gaming &amp; Leisure
---

### Post by tevettgoad on 2015-11-30
So i am fairly new to Ubuntu and im trying to install Steam but it wont launch and the terminal gives me this error message, can someone help me make heads or tails of this and get me pointed in the right direction to fix it? im running the 14.04.3 Version
The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.5)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue:

---

### Post by Bucky Ball on 2015-12-01
*Thread moved to **Gaming & Leisure**.*

Welcome. ***Installations and Upgrades*** is for issues installing or upgrading the OS. Good luck.

---

### Post by oldrocker99 on 2015-12-01
Did you try: ```

sudo apt-get install -y steam
```

That has worked for me with every Ubuntu distro. If not that, go to [steampowered.com](steampowered.com) and download **steam_latest.deb**. It *should* work. If not, try this:```
sudo apt-get -f install
```

Post your results, please.

---

### Post by MeagerWyrm on 2015-12-01
Due to my impatience with the prompts I selected *I disagree* in the user agreement prompting (logically anyway). This time I tried it again and carefully read through the prompts and this piece of code worked just fine, thank you!
sudo apt-get install -y steam

Edit: Well that's nice.. why do I have 2 additional (and identical) posts?

Edit2: Well, that was quick, thanks for removing my additional posts!

---

### Post by tevettgoad on 2015-12-01
Oldrocker, the first set of code worked like a charm. Thank you

---

### Post by Bucky Ball on 2015-12-02
If fixed, please see the first link in my signature. Enjoy! :)

---

