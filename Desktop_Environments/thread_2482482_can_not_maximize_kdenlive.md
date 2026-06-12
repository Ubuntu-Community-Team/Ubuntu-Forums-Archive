---
title: "can not maximize kdenlive"
date: 2023-01-01
forum: Desktop Environments
---

### Post by ksso on 2023-01-01
hi
just cant maximize in order to browser the bottom part of the window, can not vertical resize it also
just need to install and open and you will see it can not be used
thanks a lot



[https://ibb.co/XWM58mT](https://ibb.co/XWM58mT)

---

### Post by mIk3_08 on 2023-01-02
Please run the command below and paste the results wrap with code here in thread. Regards and cheers
```
snap list
```

---

### Post by ksso on 2023-01-02
Nombre             Versión          Rev    Seguimiento      Editor      Notas
bare               1.0                   5      latest/stable    canonical&#10003;  base
core               16-2.57.6          14399  latest/stable    canonical&#10003;  core
core20             20221212         1778   latest/stable    canonical&#10003;  base
firefox            108.0.1-1         2211   latest/stable/&#8230;  mozilla&#10003;    -
gnome-3-38-2004    0+git.6f39565    119    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes  0.1-81-g442e511  1535   latest/stable/&#8230;  canonical&#10003;  -
snapd              2.57.6           17883  latest/stable    canonical&#10003;  snapd
woe-usb            v3.3.0           21     latest/edge      ernytech    -

---

### Post by tea for one on 2023-01-02
From your screenshot, it looks like you are using Xubuntu with xfce.
This link will give you keyboard shortcuts.
[https://docs.xfce.org/xfce/xfwm4/getting-started#resize_windows](https://docs.xfce.org/xfce/xfwm4/getting-started#resize_windows)

The attached image will show you the position of another Window Control in the top left of the title bar (to also resize windows)
Your screenshot shows a V in the top left.

---

### Post by ksso on 2023-01-02
ok
yes I have tried with mouse and keyboard shortcut but it does not maximise, even at full screen doesnt show lower part that is needed to access for more option to run the programme; the resize only work horizontal but not vertically
another kde app like okular allows to maximise and resize

---

### Post by deadflowr on 2023-01-02
It's common practice to post what release is in use, what desktop is in use, and what version of the package is in use.
post back the results from
```
lsb_release -a; echo $XDG_SESSION_DESKTOP; apt policy kdenlive
```

We only assume, unless told otherwise, that this is Ubuntu Desktop, and not any other flavor.

---

### Post by tea for one on 2023-01-02
> **ksso said:**
> yes I have tried with mouse and keyboard shortcut but it does not maximise,
Your screenshot shows the kdenlive window as larger than your screen.
Therefore, you have to reduce the size first, then maximise to fit.

From the weblink:-
"you can use the Alt-Right Click shortcut while you hold the mouse pointer anywhere over the window frame; it will act as if you were dragging the bottom-right corner of the window"

---

### Post by ksso on 2023-01-02
that shows a menu but doesnt maximise nor resize with that menu or holding the mouse to show the lower part because vertical resizing doesnt work, 
krita does well...

---

### Post by tea for one on 2023-01-02
> **ksso said:**
> that shows a menu but doesnt maximise nor resize with that menu or holding the mouse to show the lower part because vertical resizing doesnt work, 
krita does well...
Alt-Right Click does not show a menu.
I do not think that you have used it correctly.

---

### Post by ksso on 2023-01-02
Hi,

I missed a post, sorry:
$ lsb_release -a; echo $XDG_SESSION_DESKTOP; apt policy kdenlive
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy
xubuntu
kdenlive:
  Instalados: 4:21.12.3-0ubuntu1
  Candidato:  4:21.12.3-0ubuntu1
  Tabla de versión:
 *** 4:21.12.3-0ubuntu1 500
        500 [http://co.archive.ubuntu.com/ubuntu](http://co.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages
        100 /var/lib/dpkg/status


I have tried forementioned options but the lower part cant be seen
here is a link to explain what happens:
[https://youtu.be/NY-nh_TmLHY](https://youtu.be/NY-nh_TmLHY)

---

### Post by #&amp;thj^% on 2023-01-02
Sorry for the party crash, I had the same issue on Kaisen linux. I tried both installing using apt and the app image. Didn't work. I went to "View" - > Dock Area Orientation, Then chose Arrange Dock Areas in Columns. Then I was able to resize.
See screenshot
Hope that helps, and kind of an iffy method.
Forgot to mention as well there is a slightly older version on flatpak to think about.
```
>> flatpak search kdenlive
Name         Description     Application ID      Version    Branch    Remotes
**Kdenlive     Video Editor    org.kde.kdenlive    22.12.0    stable    flathub**


me on Mon Jan 02 at 11:27 AM in ~ branch: (HEAD) 
>> apt policy kdenlive
kdenlive:
  Installed: [COLOR="#FF0000"]22.12.0-1[/COLOR]
  Candidate: 22.12.0-1
  Version table:
 *** 22.12.0-1 500
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by tea for one on 2023-01-02
> **1fallen said:**
> Sorry for the party crash
Party crashers welcome.
Especially, when a new variety of beverage is put in the punchbowl.

---

### Post by ksso on 2023-01-02
Thank you, now can be used!

---

### Post by #&amp;thj^% on 2023-01-02
> **ksso said:**
> Thank you, now can be used!

Your welcome, and as said, kind of a iffy work-around, but.....
> **tea for one said:**
> 
Especially, when a new variety of beverage is put in the punchbowl.

LOL I like that phrase ;)

---

### Post by mIk3_08 on 2023-01-03
> **ksso said:**
> Thank you, now can be used!
On how to mark this thread as solve,
Please Click the "Solve thread" link below. 
Thanks guys for the help when I was not around. You take part of me. Regards and cheers.

---

