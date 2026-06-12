---
title: "Modifying Appearance (Menu -&gt; Settings -&gt; Appearance)"
date: 2014-11-13
forum: Desktop Environments
---

### Post by OldHarry on 2014-11-13
Hi,

I would like to modify the Appearance Styles, etc., like I used to be able to do with MS Windows. The pre-defined ones in Appearance either have overly-thick window bars, garish colours, and/or make some window toolbars all black. I would like to customise all this, including fonts and sizes.

I have already tried to do this through Appearance. I also tried to do this by loading Razor Appearance Configuration and GNOME Colour Chooser through the Ubuntu Software Centre. Razor did not appear to make any difference, while GNOME didn't seem to apply to Ubuntu.

I would be very grateful if someone could direct me to the right application or a previous post.

Ta.

---

### Post by grahammechanical on 2014-11-13
What version of Ubuntu or its flavours are you using? It does not seem to me that you are using the same User Interface face as me. And I cannot guess the UI on your system.

Regards.

---

### Post by ibjsb4 on 2014-11-13
To verify the desktop and version, in terminal:
```
echo $DESKTOP_SESSION
```
and
```
lsb_release -a
```

---

### Post by OldHarry on 2014-11-14
Thank you for replying.

We recently installed Ubuntu 14.04.01 LTS Trusty Tahr. We immediately replaced Unity with the Xfce 4.01 Desktop Environment. I can't abide not having a decent menu system.

I hope that's helpful.

---

### Post by OldHarry on 2014-11-14
> **ibjsb4 said:**
> To verify the desktop and version, in terminal:
```
echo $DESKTOP_SESSION
```
and
```
lsb_release -a
```

Thanks ibjsb4

I already used the sudo code to discover which version of Ubuntu I have. I discovered which version of Xfce I have by pressing the About button in Menu. :D

Because you went to all the trouble of writing to me, I did type in the first command. The Terminal merely listed the Desktop Session as 'xfce'.

I really appreciate the help. I might have been completely unfamiliar with Ubuntu and a new user.

Ta.

---

### Post by ibjsb4 on 2014-11-14
You tagged your thread [ubuntu], should of tagged it xubuntu (xfce).

Anyhow, I do not run xfce so I'm not much help, but here's a couple of links.

[https://wiki.xfce.org/howto/customize-menu](https://wiki.xfce.org/howto/customize-menu)
[https://www.google.com/search?client=ubuntu&channel=fs&q=customize+xubuntu+xfce&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=customize+xubuntu+xfce&ie=utf-8&oe=utf-8)
[https://www.google.com/search?client=ubuntu&channel=fs&q=customize+fonts+xubuntu+xfce&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=customize+fonts+xubuntu+xfce&ie=utf-8&oe=utf-8)

Good luck :)

---

### Post by Frogs Hair on 2014-11-15
If you installed XFCE and not the the Xubuntu desktop the xfce4-goodies provides additional panel indicators and xfwm4-themes package has additional themes as well as xfce4-artwork package. all three are in the repository/software center.

---

