---
title: "checkinstall"
date: 2009-01-29
forum: General Help
---

### Post by anv on 2009-01-29
I have had problems with checkinstall command. I installed lately Pidgin and Inkscape from souce but I couldn't manage to get the process done with checkinstall I had to use the conventional method (make install). Does someone know possible package dependencies which I might lack or other explanation for my bad luck with checkinstall

---

### Post by albinootje on 2009-01-29
> **anv said:**
> I have had problems with checkinstall command. I installed lately Pidgin and Inkscape from souce but I couldn't manage to get the process done with checkinstall I had to use the conventional method (make install). Does someone know possible package dependencies which I might lack or other explanation for my bad luck with checkinstall

Checkinstall produces logfiles, which it will also mention when the installation fails.

Here's an example about what can go wrong :
Earlier this week i've used checkinstall for some compilation and it bailed out because the package version numbering in the (afterwards) resulting deb package was not correct. After editing the package version number it worked fine.

---

### Post by anv on 2009-01-29
where I can find logs?

ok I think I did understand, it were actually same problem here, the numbering were something which didn't work with dpkg so after editing version number it started to pack.

---

### Post by albinootje on 2009-01-29
> **anv said:**
> where I can find logs?

Checkinstall should tell you where to find the checkinstall log file the moment that creation and installation of the deb package by checkinstall fails.

---

### Post by mc4man on 2009-01-29
It's not always possible to use checkinstall. Using this will increase your chances (there is a bug in checkinstall this addresses

```
sudo checkinstall --fstrans=no
```

Also sometimes if you had to do a make install but would like to get rid of the build folder you can cd back to your build folder and run this
```
sudo checkinstall --fstrans=no --install=no
```

If successful then run from build folder
 
sudo make uninstall

Then use your .deb to install and afterwards delete the build folder

---

### Post by anv on 2009-01-29
thanks this was all I needed

---

