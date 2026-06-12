---
title: "Run X Application without Desktop Environment"
date: 2020-10-09
forum: Desktop Environments
---

### Post by giobaxx on 2020-10-09
[URL="https://unix.stackexchange.com/posts/613782/timeline"]
[/URL]

I'm tryng to configure a Linux to work as a kiosk by running google-earth only and I'm just following a guide about how to run it Without Desktop Environment that it would be perfect for me:

[https://linuxconfig.org/how-to-run-x-applications-without-a-desktop-or-a-wm](https://linuxconfig.org/how-to-run-x-applications-without-a-desktop-or-a-wm)

Basically if i boot in multi-user.target running from a Terminal this command:

```
xinit google-earth-pro $* -- :0 vt$XDG_VTNR

```

i'm able to open google-earth-pro but it will not run in full screen, and the actual window seems to be no resizable, even pressing F11.

In this workstation there is a NVIDIA Card but the driver are't still installed it could be this the problem?

Thanks

---

### Post by QIII on 2020-10-09
Please use the default font.  Also use code tags around commands and their results rather than quote tags.

To use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

