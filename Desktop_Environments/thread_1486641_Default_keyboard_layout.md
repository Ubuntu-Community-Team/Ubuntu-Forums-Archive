---
title: "Default keyboard layout"
date: 2010-05-18
forum: Desktop Environments
---

### Post by moody_cz on 2010-05-18
Hi everyone,

I've installed Ubuntu Lucid Lynx for my friend from Moldova, added there a romanian localization via Language support and removed English. 

Then, I wanted to set default keyboard layout to Romanian, so I moved it up above the US layout. However, after reboot I always had US keyboard layout selected in Gnome. 

So I removed US keyboard layout and left there only Romanian one. But, surprisingly, US layout always appears after reboot and is selected by default.

How to solve this?

Thanks in advance.

---

### Post by Tkdboy on 2010-05-18
Hi

Im not sure if u can remove US layout.
As far as I know you can change your default Language from :
System->Preferences->Keyboard->Layout.

---

### Post by moody_cz on 2010-05-19
> **Tkdboy said:**
> Hi

Im not sure if u can remove US layout.
As far as I know you can change your default Language from :
System->Preferences->Keyboard->Layout.

Thanks for your reply. Anyway, that's weird if one can't remove US layout. How to set a default layout? By moving it to the top? I did so (as I wrote before) and still US layout is selected by default so far.

---

### Post by moody_cz on 2010-05-20
Really? No one?

---

### Post by maedox on 2010-05-20
Set your layout like you want it and click the "Set system wide" button on the lower right. If it does not work there may be a permission problem where the config is stored. Why didn't you select the layout you wanted in the installation wizard?

---

### Post by moody_cz on 2010-05-20
> **maedox said:**
> Set your layout like you want it and click the "Set system wide" button on the lower right. If it does not work there may be a permission problem where the config is stored. Why didn't you select the layout you wanted in the installation wizard?

Of course I did click the "Set system wide" button, but it acted the same way. If it's a permission problem, where to check for a log file?

I didn't select the desired layout in the installation as I really didn't know what language the user'll use. And, I prefer US layout myself, so I left it there as I was suppose to make several settings.

Ty for your time.

---

### Post by bbordwell on 2010-05-25
The problem is that GDM does not know about the change in default keyboard layout, to fix the problem, log out change the keyboard layout to the one desired, log back in, then remove the original keyboard layout from keyboard preferences. From now on the us keyboard layout should be gone.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/530999](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/530999)

---

### Post by Bouke on 2010-11-05
Thank you, I was getting very frustrated with the keyboard layout's constant revival from /dev/null!

---

