---
title: "problems with desktop icons (xubuntu 16.04)"
date: 2016-07-14
forum: Desktop Environments
---

### Post by jomasol on 2016-07-14
hi

I have just installed a new Xubuntu 16.04 on my pc. I have downloaded last updates from repository and change the original theme to Numix and Numix circle for icons. Here is my problem: once I have changed the theme the desktop icons appears with a shadow (not in all icons but some of them); this shadow is just not under the text but moved to the right (see image).

any solution?

best regards. 


[http://i.imgur.com/IHbhals.png](http://i.imgur.com/IHbhals.png)

---

### Post by Toz on 2016-07-14
See: [http://ubuntuforums.org/showthread.php?t=2330711&p=13517153&viewfull=1#post13517153](http://ubuntuforums.org/showthread.php?t=2330711&p=13517153&viewfull=1#post13517153).

---

### Post by jomasol on 2016-07-14
hi Toz

thanks for your help. I have tried to follow your steps but I have no positive results. I have the gtk2-engines-murrine_0.98.2-0ubuntu2 in  /var/cache/apt/archives but nothing new appears on my desktop :(

---

### Post by Toz on 2016-07-14
> **jomasol said:**
> hi Toz

thanks for your help. I have tried to follow your steps but I have no positive results. I have the gtk2-engines-murrine_0.98.2-0ubuntu2 in  /var/cache/apt/archives but nothing new appears on my desktop :(

Did you install the file via dpkg? Have you logged out and back in again?

What do the following return:
```
ls -l /var/cache/apt/archives | grep gtk2-engines-murrine
```
...and
```
apt-cache policy gtk2-engines-murrine
```

---

### Post by Toz on 2016-07-14
According to [https://github.com/numixproject/numix-gtk-theme/issues/492]("https://github.com/numixproject/numix-gtk-theme/issues/492"), you can also edit /usr/share/themes/Numix/gtk-2.0/gtkrc and change line 531 to read "textstyle = 0".

---

### Post by ka55o5 on 2016-07-14
> **jomasol said:**
> [..] but I have no positive results.
How about *not using* the affected theme, because wouldn't that be -just- **so** much easier? o.0

> **Toz said:**
> It also only appears to affect some themes [..]

**Edit**: It's a (classified) bug, so why not work around it - instead of trying to adapt the entire system to it...

---

### Post by jomasol on 2016-07-14
hi, 

changing line 531 works perfect! my desktop works fine and icons look better. thanks!

---

