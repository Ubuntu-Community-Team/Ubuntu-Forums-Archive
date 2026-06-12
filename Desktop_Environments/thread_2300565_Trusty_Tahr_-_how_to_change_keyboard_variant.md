---
title: "Trusty Tahr - how to change keyboard variant?"
date: 2015-10-26
forum: Desktop Environments
---

### Post by oui on 2015-10-26
Hi

I did test minimal lubuntu 15.10 and it works but lubuntu Trusty Tahr works better...

As I have to wait probably until April 2016 to become a better one. and LTS probably over that, I will try to eliminate my last problems using  lubuntu Trusty Tahr ;)

My problem is, that my keyboard uses the layout «us intl»

How to install that layout on lubuntu Trusty Tahr?

Kind regards

---

### Post by Rex Bouwense on 2015-10-28
On your LXPanel on the right side is an icon that looks like a keyboard, right click it and then select Preferences from the pop up menu.  A new window will open up.  Select the second tab, Input Method.  Navigate to Select an input method.  Choose English and when the menu opens choose English International.  Select add.

---

### Post by oui on 2015-10-29
Hi Rex

> **Rex Bouwense said:**
> On your LXPanel on the right side is an icon that looks like a keyboard, right click it and then select Preferences from the pop up menu.  A new window will open up.  Select the second tab, Input Method.  Navigate to Select an input method.  Choose English and when the menu opens choose English International.  Select add.

thank you for your detailed answer but my lubuntu minimal desktop looks probably different: They are 4 little icons on the right side. They are sound, us, 23:39 and I/O

if I hit right key on US, a menu appears. the top line introduces "keyboard layout handler" settings

opting for it 

- I have to unmark the field "keep system layouts"
- the keyboard layout list shows flag US, layout US, variant empty
- key + Add permit to enter a second time US ):P

if I enter some us intl in the line field  "Advanced setxkbmap options", I can enter us intl and that entry seems to be registered but nothing happens :mad: ...

This "keyboard layout handler" is really nothing goods: It was so easy to do that directly in /etc/X11/xorg.conf ;) : nothing to search, restart and never errors!

---

### Post by Rex Bouwense on 2015-10-29
You should be able to get to IBus Preferences through the main menu->Preferences->Keyboard Input Methods.

---

