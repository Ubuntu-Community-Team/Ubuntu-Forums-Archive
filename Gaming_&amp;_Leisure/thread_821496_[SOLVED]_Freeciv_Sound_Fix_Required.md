---
title: "[SOLVED] Freeciv Sound Fix Required"
date: 2008-06-07
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-06-07
Hi,
I have no sound in freeciv.
I have download the file at: [ftp://ftp.freeciv.org/freeciv/contrib/audio/soundsets/]("ftp://ftp.freeciv.org/freeciv/contrib/audio/soundsets/")

What directory must I put this file in?

Thanks.

---

### Post by Rytron on 2008-06-09
I found this thread: [http://ubuntuforums.org/showthread.php?t=245876]("http://ubuntuforums.org/showthread.php?t=245876")

Solved.

---

### Post by ntg on 2011-02-09
```

    wget http://download.gna.org/freeciv/contrib/audio/soundsets/freesounds-1.3.1.zip
    sudo unzip freesounds-1.3.1.zip -d /usr/share/games/freeciv/
    freeciv -S freesounds

```

Will solve the problem...
Sounds are not included for licencing reasons...
You can replace the wget on the dataset with the newest/one you prefer...
See other posts for details ([http://freeciv.wikia.com/wiki/Sounds](http://freeciv.wikia.com/wiki/Sounds))

---

