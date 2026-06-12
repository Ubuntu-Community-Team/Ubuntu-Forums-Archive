---
title: "can't paste anything on my desktop !!!"
date: 2009-01-14
forum: Desktop Environments
---

### Post by dungpt on 2009-01-14
i can't paste anything to my desktop?
what's goin on?

and with thunar file browsing, why itsn't cut my file name when it's too long?

---

### Post by mali2297 on 2009-01-14
Go to *Settings Manager* and then *Desktop*. Check that the option *Allow Xfce to manage the desktop* is enabled.

As for the long file names not being cut, I don't know.

---

### Post by dungpt on 2009-01-15
> **mali2297 said:**
> Go to *Settings Manager* and then *Desktop*. Check that the option *Allow Xfce to manage the desktop* is enabled.

As for the long file names not being cut, I don't know.

it's checked.
i can create new file , drag drop, delete....

but i **CAN"T FIND THE PASTE OPTION (CTRL+V)** to paste my file to my desktop (except drag drop it to my desktop)

CRAZY

---

### Post by adamlau on 2009-01-15
I am assuming you are referring to the quirky 'clipboard' (versus KDE/GNOME) and the lack of icon text wrapping support. That is how it is with Xubuntu and Xfce in general :) . Regarding the 'clipboard' issue, perform cut/copy/paste operations within Thunar without performing intermediate actions in between. It is this very quirkiness which leads more than a few Xfce users to install the xfce4-clipman-plugin :) . Besides, you could always use cp and mv. The desktop icon text wrapping issue continues to persist in Xfce 4.6 (at least up to svn-29116). Filing a bug report is your best bet towards a speedy resolution to this annoyance.

---

### Post by dungpt on 2009-01-15
exactly, how can i paste my file to desktop?

---

### Post by stevoo on 2009-01-15
Ctrl+c the file that you want -> copy 
Ctcl+p on the desktop -> paste

or right click select copy
right click on desktop select paste

maybe you didnt actually manage to copy the folder ! 
none of this work ?

---

### Post by dungpt on 2009-01-15
CTRL + P hasn't effect on my desktop :|
but i only can drag & drop my file or create new file on it

---

### Post by ubhi on 2009-01-15
If ctrl+v not working.. then you can check by going manually to desktop by open the folder of desktop something like
/home/youprofilename/Desktop/
then try to paste items... & check security by goint to terminal & check desktop directory security by pressing ls -l do you have full access to desktop directory

---

### Post by dungpt on 2009-01-15
> **ubhi said:**
> If ctrl+v not working.. then you can check by going manually to desktop by open the folder of desktop something like
/home/youprofilename/Desktop/
then try to paste items... & check security by goint to terminal & check desktop directory security by pressing ls -l do you have full access to desktop directory

i open my desktop folder with thunar, i CAN paste anything to it.
but on my desktop , i CAN"T

---

### Post by dungpt on 2009-01-15
no one help? there's noway to paste file on my xubuntu desktop ?

---

