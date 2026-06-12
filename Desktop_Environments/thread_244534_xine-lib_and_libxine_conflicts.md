---
title: "xine-lib and libxine conflicts"
date: 2006-08-26
forum: Desktop Environments
---

### Post by pickarooney on 2006-08-26
Any time I try to install a program via apt-get I get the following error:```

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libxine-extracodecs: Depends: libxine-main1 but it is not going to be installed
  totem-xine: Depends: libxine-main1 (>= 1.1.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


When I try to install amsn, I get this
```

The following packages have unmet dependencies:
  amsn: Depends: imlib11 but it is not going to be installed
        Depends: docker but it is not going to be installed
        Depends: tcltls but it is not going to be installed

```

Anyone know how to solve this? My sources lists is as follows

---

### Post by pickarooney on 2006-08-26
Actually, nothing is installing any more. Everything I try to apt-get throws up the same error along the lines of:  abcde: Depends: cd-discid but it is not going to be installed

Isn't it supposed to go look for and install the dependent packages??

---

