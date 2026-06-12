---
title: "Kubuntu + pt_BR = problem with acentuation and perl"
date: 2006-01-04
forum: General Help
---

### Post by Mergulhao on 2006-01-04
My perl scripts always show this message:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "pt_BR:pt:pt_PT",
        LC_ALL = (unset),
        LANG = "pt_BR.ISO-8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

My KDEapps(OO2 is ok) displays an "C_cedilla" with accute like this: &#263;. When I change the LANG to ISO-8859-1(default is UTF8) KDE goes ok, but firefox not yeat.

I dont know what to do. Any help?

---

### Post by fdoving on 2006-05-10
Hi.
Try this in a terminal:
```

sudo dpkg-reconfigure -plow locales

```

---

