---
title: "Starts up in terminal"
date: 2013-08-05
forum: Desktop Environments
---

### Post by life in color on 2013-08-05
I've been using Natty Narwhal on my computer for well over a year and decided to upgrade to Precise Pangolin. For a few months everything was fine, but recently (about) every other time I turn on my computer it boots to terminal rather than GUI. I tried <ctrl><alt><f7> when it booted to terminal and the result was
```
saned disabled; edit etc/default/saned
*checking battery state...
```. Please help.

---

### Post by life in color on 2013-08-24
This is a persistent problem which I fear could lead to me losing the ability to boot with GUI. Please help!

---

### Post by tgalati4 on 2013-08-24
Open a terminal and look for error messages:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  You might have a graphics chip issue that is dropping you to a terminal.  Look for xorg errors:

```
more /var/log/Xorg.0.log
grep EE /var/log/Xorg.0.log
```

Many hardware issues look like software issues, so you will need to spend some time try to separate them.

---

### Post by ibjsb4 on 2013-08-24
You could also enable boot.log and see what comes up.

```
sudo gedit /etc/default/bootlogd
```

And change the No to a yes.

Then look in /var/log/boot.log next time it happens.

---

