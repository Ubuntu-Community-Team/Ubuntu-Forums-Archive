---
title: "bad resolution"
date: 2007-02-02
forum: Desktop Environments
---

### Post by bosshoof on 2007-02-02
[SIZE="4"]hello every body
i'm a new linux <ubuntu> user
and the resolution of the screen is automatically set to (1280*1024)
and every time i make it 1024*768 it does it and changes for a second and then
suddenly 
i'm automatically logged off
and the resolution is 1280*1024 again
please tell me what to do
as my eyes are in hurt due to the bad refresh rate

thanks in advance[/SIZE]

---

### Post by kc0dhb on 2007-02-05
Do you have a proprietary video card (nvidia, ati)?

If you don't, or are fine using the free driver i would run the following in a terminal

```

sudo dpkg-reconfigure xserver-xorg

```

(Most of the defaults should work)

And in there set the resolutions that you want.  Then you are going to have to logout and restart your xserver (ctrl alt backspace).

If for some reason it doesn't work,  you will want to ctrl alt F1 (or any F key through F6), login and do the following.

```

cd /etc/X11
sudo cp xorg.conf xorg.conf.notworking
ls
sudo cp xorg.conf.20070203193321 xorg.conf

```

Where xorg.conf.20070203193321 is a date stamp that you will see by the ls command.  use the tab completion so you don't have to type it all out.

If you don't understand (or it was unclear) anything I said above, don't hesitate to ask.
If the above doesn't work please past the output of

```

lspci
cat /etc/X11/xorg.conf

```

Enjoy

---

