---
title: "problem with theme (GTK 2.X) in 9.04"
date: 2009-05-06
forum: Desktop Environments
---

### Post by livedlooz on 2009-05-06
i got problem with some parts of the theme(GTK 2.X) i installed.. the theme didnt work on "downloading package files" window and its progress bar.. i dont know if im the only with this kind of bug.. btw im using the lasted Ubuntu 9.04

---

### Post by mcduck on 2009-05-06
> **livedlooz said:**
> i got problem with some parts of the theme(GTK 2.X) i installed.. the theme didnt work on "downloading package files" window and its progress bar.. i dont know if im the only with this kind of bug.. btw im using the lasted Ubuntu 9.04

Most likely your problem is that you have downloaded the theme yourself, and installed it in your user's own theme directory. And the programs that don't get correct theme are the administrative tools that actually run as root user, not your own user. As root doesn't have those themes, root apps can't use them either and fall back to default theme instead.

If this sounds about correct explanation for your problem, then the fix is easy. Just run the following commands in a terminal to link your theme directories into root's ones:

```
sudo ln -s /home/yourusername/.themes /root/.themes
sudo ln -s /home/yourusername/.icons /root/.icons
```

Now root will always have the same themes available you install for your normal user. Of course the alternative is to just install the themes system-wide, into /usr/share/themes, instead of using the user's personal theme directory.

---

