---
title: "night mode for LXQT (Lubuntu)"
date: 2019-11-07
forum: Desktop Environments
---

### Post by a0rahmati on 2019-11-07
Hello.

There are some applications for Android, Windows, ... which change the colors of the screen and make them warmer with lower blue light to protect eyes.
I'm looking for an application like them that works on LQXT (Lubuntu).

Thanks.

---

### Post by guiverc on 2019-11-07
I use `redshift` myself.   If you want a panel icon (worth it in my opinion), add the `redshift-gtk`package as well.

Please note there is also a `redshift-qt` package in test currently, which will be more resource efficient for LXQt  ([https://phab.lubuntu.me/T78](https://phab.lubuntu.me/T78)) It's available for use via PPA, but I've not yet tried it as the packaging currently is only for 19.10 not my 20.04).  If you're running 19.10 I would consider using that; [https://launchpad.net/~hmollercl/+archive/ubuntu/redshift-qt](https://launchpad.net/~hmollercl/+archive/ubuntu/redshift-qt)

```
guiverc@d960-ubu2:~$   apt-cache search redshift
..
redshift - Adjusts the color temperature of your screen
redshift-gtk - Adjusts the color temperature of your screen with GTK+ integration
..

```

---

### Post by a0rahmati on 2019-11-08
Thank you for your answerguiverc.

I installed redshift.[**[COLOR=#DD4814][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=2074246")

---

