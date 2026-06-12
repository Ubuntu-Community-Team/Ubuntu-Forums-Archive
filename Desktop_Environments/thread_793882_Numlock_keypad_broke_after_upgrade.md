---
title: "Numlock keypad broke after upgrade"
date: 2008-05-14
forum: Desktop Environments
---

### Post by bluedog800 on 2008-05-14
I upgraded my wifes computer yesterday to ubuntu 8.04, now after the upgrade the numlock keypad stopped working, the light would toggle, but that would still not help in getting it to type.  I tried a few different layouts in System -> Preferences -> Keyboard, generic 104 i would have thought would work.  The keyboard does work in terminal if you Ctrl-Alt-F1 for example, so it is a gnome thing!?!, i tried to do a dpkg-reconfigure xserver-org but that didn't help

I also tried copying my old xorg.conf file in to place but also didn't change.

It is PS2 keyboard hp KB-0316

Thanks

---

### Post by bluedog800 on 2008-05-16
During the upgrade an assistive feature was turned on

System -> Preferences -> Assistive Technologies -> Keyboard Accessibility -> Mouse Keys, uncheck Allow to control the pointer using the keyboard.

Hope this can help someone else in the future.

---

### Post by enoksrd on 2009-02-26
I'm on 8.10 on a laptop, and a few days ago my external usb keyboard started always being in numlock mode when I log into ghome.  Two major problems:

1. It's a compact keyboard with the numeric keypad superimposed on the alphanumeric/regular keypad.  So when numlock is on I can't use uiopjkl;m or /

2. I can't seem to turn off numlock using the keyboard.  There's a numlock button, but it doesn't seem to do anything.

I managed to get the external keyboard back into non-numlock mode by toggling the numlock key on the laptop builtin keyboard, and maybe unplugging and replugging the external keyboard.

Today it was even more screwed up, with the superimposed numeric keys now controlling the mouse.  Googling got me to your suggestion, which got me back to numeric superimposed keys :P  I have no idea why this works, but I was able to get back normal keys by checking

System->Preferences->Keyboard->Layout->Other Options->Use keyboard LED to show alternative layout->Numlock LED shows alternative layout

and that fix persists across logouts.

Note: The problem only starts *after* U log into gnome.  On the gdm login screen numlock is always off.

---

### Post by NT4usB on 2009-03-23
> **bluedog800 said:**
> During the upgrade an assistive feature was turned on

System -> Preferences -> Assistive Technologies -> Keyboard Accessibility -> Mouse Keys, uncheck Allow to control the pointer using the keyboard.

Hope this can help someone else in the future.

It did, Thanks!

---

### Post by Claus7 on 2010-01-13
Hello,

> **bluedog800 said:**
> During the upgrade an assistive feature was turned on

System -> Preferences -> Assistive Technologies -> Keyboard Accessibility -> Mouse Keys, uncheck Allow to control the pointer using the keyboard.

Hope this can help someone else in the future.

Thank's a lot!

Regards!

---

### Post by ae+ on 2010-06-16
> **bluedog800 said:**
> During the upgrade an assistive feature was turned on

System -> Preferences -> Assistive Technologies -> Keyboard Accessibility -> Mouse Keys, uncheck Allow to control the pointer using the keyboard.

Hope this can help someone else in the future.

This has been driving me CRAZY. Thanks heaps. I haven't logged on here for 18 months, but did to give a big thanks :)

---

### Post by NT4usB on 2010-06-17
Coincidence, that this thread comes around again.
Nums just stopped working on this box. It's been up 4 days, and they worked fine until tonight.
How/why/what sort of magic causes Mouse Keys bla to become checked on a machine I use every day for a year?

---

### Post by kyle98 on 2010-06-19
Hello, 

If its your laptop keyboard key that has  broken , you don't need to worry that you'll need a whole new keyboard. 

I got my laptop keys replaced by this company at Ebay. They gave me 5 key sets at a very reasonable price. And they have installation video's which makes it really easy to fix the keys
[http://www.laptopkey.com]("http://www.laptopkey.com")

---

### Post by wsscott on 2010-06-30
I had the same problem.  

Thanks!

---

### Post by BobHur on 2010-07-06
Thanks, I picked up the same problem when upgrading to 10.4.

I can see the point of defaulting to mouse keys for those who need that kind of assistance, but a brief on-screen note about this and how to change it back during/after the install or upgrade would be appreciated.

---

### Post by mattmetzger on 2010-09-21
**dup**

---

### Post by mattmetzger on 2010-09-21
**Shift+NumLock**

---

