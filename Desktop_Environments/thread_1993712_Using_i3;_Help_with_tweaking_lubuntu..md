---
title: "Using i3; Help with tweaking lubuntu."
date: 2012-06-02
forum: Desktop Environments
---

### Post by LiamOS on 2012-06-02
Hi,

For quite some time, I've been using i3 on my netbook, but haven't yet transfered it over to my main computer due to its lack of general functionality. In lubuntu, I noticed the option to change the default window manager, so I changed it to i3 in a virtual machine and I'm loving what I see for the most part.

The only main problem I currently have is that PCManFM controls the desktop, and seems to be required by the parts of LXDE I want(Bar, session management, etc.).
Edit: I've also tried messing about with the config files in .config with no success.

Does anybody know how to remove this functionality from PCManFM, or how to replace it with a more agreeable file manager?

Thanks.

---

### Post by LiamOS on 2012-06-03
I have the issue semi-solved.
I added 
```
exec killall pcmanfm
```
to my i3 config file.

---

### Post by mikewhatever on 2012-06-03
Check out the output of 'pcmanfm --help', it has some desktop related options.

---

### Post by LiamOS on 2012-06-04
Thanks!

The solution's been improved to including 
```
exec pcmanfm --desktop-off
```in my i3 config.


Edit:
This is no longer terribly good when using Feh. However, using killall as in the first solution works nicely.

---

