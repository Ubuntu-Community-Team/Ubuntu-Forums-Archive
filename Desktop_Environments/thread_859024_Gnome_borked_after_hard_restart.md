---
title: "Gnome borked after hard restart"
date: 2008-07-14
forum: Desktop Environments
---

### Post by shiznatix on 2008-07-14
Howdy. The other day I was having problems with Gnome and after it froze while I was trying to restart I just did a hard reboot. Now, when I try to login normally, it starts to load but ends up in a white screen and freezes.

It goes from the ubuntu orange color screen, then it looks like Gnome is going to load and has a black background and a lighter area where my taskbars are, then it goes to all white and thats it. The only way to boot up now is to run "fail safe Gnome."

I am not quite sure what I was doing that froze up Ubuntu in the first place but I think the problem might have something to do with desktop effects. I usually have it on "make my computer flashy and fun" but now in fail safe Gnome it won't let me switch the effects on.

Any guidance on this issue would be a great help. Thanks.

---

### Post by Tomatz on 2008-07-14
Sounds like a gpu driver problem. What graphics card do you have?

---

### Post by shiznatix on 2008-07-14
lspci says this:

> 01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)

---

### Post by Tomatz on 2008-07-14
Hmmm

Before we start trying to install things from the cli try this:

Login to gnome and when the "white screen" pops up and everything seems fully loaded press **alt f2** (you obviously wont be able to see anything), **wait 10 seconds** then type:

```
metacity --replace
```

Press **return**

Hopefully this will disable compiz which is using the suspected borked drivers and give you your desktop back.

---

