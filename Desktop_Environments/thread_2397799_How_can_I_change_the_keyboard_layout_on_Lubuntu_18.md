---
title: "How can I change the keyboard layout on Lubuntu 18.04?"
date: 2018-08-03
forum: Desktop Environments
---

### Post by Paddy Landau on 2018-08-03
On Lubuntu 16.04, I could install and use lxkeymap to change the keyboard layout. In 18.04, lxkeymap is no longer available.

On Lubuntu 18.04, lxkeymap is no longer available. I've added Keyboard Layout Handler to the panel, but all it does is display the US flag. I need the UK layout.

In case it makes a difference, I need to do this on a Live CD as well as on an installed system.

How can I change the Lubuntu keyboard layout, please?

---

### Post by Rex Bouwense on 2018-08-04
You used to be able to add/delete keyboard layouts with the Keyboard layout Handler.  First uncheck "Keep system layouts" on the right side and then select "Add" from the left side.  Select English (UK) from the pop-up window and move it to the top.  After you are finished making changes, recheck "Keep system layouts".  I believe it does require a reboot to take effect

---

### Post by Paddy Landau on 2018-08-04
Perfect, Rex, thank you! It also works on the Live CD, and doesn't need a reboot.

---

### Post by syedkazmi on 2018-08-12
How can I add Urdu keyboard?

---

### Post by wildmanne39 on 2018-08-12
Hello and welcome to the forum syedkazmi, please start your own thread and do not post in a solved thread or someone else's that way you can get the individual help you need.

Thanks

---

### Post by sysjoker on 2018-10-21
This is how I changed  the keyboard layout on Lubuntu 18.04 via terminal. If it's not easy to type this command with your current layout, copy &  paste this in terminal :)  
```
sudo dpkg-reconfigure keyboard-configuration
```

---

### Post by Paddy Landau on 2018-10-22
> **sysjoker said:**
> ```
sudo dpkg-reconfigure keyboard-configuration
```
Thank you. I'll try that next time.

---

### Post by paapu on 2019-01-08
Thanks,

```
sudo dpkg-reconfigure keyboard-configuration
```
did the trick also in xubuntu 18.04

After a fresh install of xubuntu 18.04 on my old Acer Aspire ES 11 laptop,
my keyboard was probably an us-keyboard.

I could not change it to Finnish one until this advice, so THANK'S!!!

Terveisin, Markus

---

