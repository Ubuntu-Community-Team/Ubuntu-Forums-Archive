---
title: "Steam makes the taskbar icons look damaged"
date: 2014-06-29
forum: Gaming &amp; Leisure
---

### Post by Jamerman on 2014-06-29
[ATTACH=CONFIG]254324[/ATTACH]As you can see, the icons on the taskbar have weird black marks over them. This was after playing Team Fortress 2 (Fullscreen) for the first time in a while. Sometimes this same effect happens on text, and I'm really confused what it is. I like running my games in fullscreen, so is there a solution other than using windowed mode?

---

### Post by Vladlenin5000 on 2014-06-29
Hi, welcome.

> As you can see, the icons on the taskbar have weird black marks over them.
No, sorry, I don't see it. They look normal to me. Your Chrome, OTOH, looks weird but probably is how you intended it to be.

(EDIT)

Now I see it but it isn't in the taskbar... It's in the launcher icons. This usually has to do with graphics driver (let me guess, ATI/AMD?)

---

### Post by Jamerman on 2014-06-29
After using ```
lspci | grep VGA
```
I got ```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```
At least now I know for sure that the driver is Intel. I've tried to check for update through apt-get and using the additional drivers program in the system settings, each to no avail :/

EDIT: Will do apt-get upgrade, restart and then do a full-screen steam game again, and post if it changes

---

### Post by oldrocker99 on 2014-06-29
You might want to try this:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get upgrade
```

If there's a newer Intel driver, this is a likely way to upgrade.

---

### Post by Jamerman on 2014-06-30
> **oldrocker99 said:**
> You might want to try this:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get upgrade
```

If there's a newer Intel driver, this is a likely way to upgrade.
Ah this solved it :) Cheers mate

---

### Post by oldrocker99 on 2014-07-01
Glad to hear it!

---

