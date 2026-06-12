---
title: "KDE popup notification transparency problem"
date: 2013-06-16
forum: Desktop Environments
---

### Post by sirjasonr on 2013-06-16
Hello All,
I'm running Kubuntu 13.04 with proprietary nvidia graphics drivers and (I think) after upgrading to 13.04, I've noticed that KDE popup notifications are now slightly corrupted. The transparency isn't normal and the borders don't align properly. Below is an image I took showing that this is the case.
I'm wondering if anyone knows where these problems come from and how to fix them... or in fact if a bug report should be filed.

Thanks!

Jason

[IMG]https://lh5.googleusercontent.com/-lPJM3-Rq36Q/Ub2i_HuLrKI/AAAAAAAAAdA/rw-0Qor8ijU/w1118-h622-no/DSC_0019.jpg[/IMG]

---

### Post by schnelle on 2013-06-16
You can try with resetting kwin (desktop effects) to default settings.
In Konsole:
```
rm ~/.kde/share/config/kwinrc
```

and then hit alt+f2 and type ```
kwin --replace
```

---

### Post by sirjasonr on 2013-06-16
This did the trick!

Thank you :)

---

