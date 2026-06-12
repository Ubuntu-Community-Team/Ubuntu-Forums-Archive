---
title: "Removing Amarok 2.0"
date: 2009-01-30
forum: General Help
---

### Post by Dobbie03 on 2009-01-30
I hate it, can someone please give me a walk through on how to remove it completely.

---

### Post by Boomhauer on 2009-01-30
how did you go about installing it?

---

### Post by Dobbie03 on 2009-01-30
From Synaptic I think.  I looked there to uninstall it but I saw to many Amarok 2.0 files.

---

### Post by kmac on 2009-01-30
System >> Administration >> Synaptic Package manager if you installed it from repositories or from a *.deb package.

I recommend Songbird, personally. You can download the Debian package [here]("https://help.ubuntu.com/community/Songbird").

It's developed by Mozilla, the Loving Father of Firefox. It's a browser and music player all in one. Referred to as "The Firefox of Media Players"

--Kyle

---

### Post by kmac on 2009-01-30
You can also use Applications >> Add/Remove to uninstall Amarok

---

### Post by Dobbie03 on 2009-01-30
> **kmac said:**
> You can also use Applications >> Add/Remove to uninstall Amarok

I've tried that it isn't listed on the add\remove list.  Is there anything I can use with the terminal? 

Songbird is good.

---

### Post by Boomhauer on 2009-01-30
if you installed with synaptic, try running this from a terminal ```
sudo apt-get remove amarok-nightly
```

---

### Post by marsmissionaries on 2009-01-30
> **kmac said:**
> System >> Administration >> Synaptic Package manager if you installed it from repositories or from a *.deb package.

I recommend Songbird, personally. You can download the Debian package [here]("https://help.ubuntu.com/community/Songbird").

It's developed by Mozilla, the Loving Father of Firefox. It's a browser and music player all in one. Referred to as "The Firefox of Media Players"

--Kyle

Song bird is NOT a mozilla product

---

### Post by kmac on 2009-01-30
I'm sorry, not quite a Mozilla product, but developed by the same team,

[http://www.getsongbird.com/about/](http://www.getsongbird.com/about/)

---

### Post by Dobbie03 on 2009-01-30
> **Boomhauer said:**
> if you installed with synaptic, try running this from a terminal ```
sudo apt-get remove amarok-nightly
```

Thanks anyway but that didn't work, it said it couldn't find a "nightly" package.

---

### Post by kmac on 2009-01-30
```
sudo apt-get remove -purge amarok*
```

If you dont have any programs installed with names such as "amarok-super-note-taking-program-and-not-a-media-player-dev"

:D

---

### Post by Dobbie03 on 2009-01-30
man now it says Purge is an unkown line

---

### Post by Boomhauer on 2009-01-30
kmac meant to say
```
sudo apt-get remove --purge amarok*
```

---

### Post by kmac on 2009-01-30
sorry, my mistake. eh, don't need purge. just do
```

sudo apt-get remove amarok*
```

---

### Post by kmac on 2009-01-30
Thanks, Boom... missed a '-' :)

---

### Post by Dobbie03 on 2009-01-30
Thanks guys, you've both been a great help.  The hated Amarok 2.0 has been purged.

---

