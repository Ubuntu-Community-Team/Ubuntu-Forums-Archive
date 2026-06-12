---
title: "really n00b question about beryl...."
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by Trianth on 2007-05-21
Umm...how do I work it? :p

I have direct rendering enabled, which I think is one requirement, right?

So...I can run the Settings Manager, but apart from that I have no idea how to work anything or get all of the cool visual effects working :redface:

---

### Post by kragen on 2007-05-21
From what I remember about Beryl, to activate the effects, you need to right click on the Beryl icon, and somehow select Beryl as the window manager.

You probably also want to select Emerald as the window decorator.

If the options aren't there, you have done something wrong - likely AIGLX isn't installed properly, or something is missing from your xorg.conf

---

### Post by Trianth on 2007-05-21
And already I have a problem...


...I can't select Beryl as my window manager.  When I try, the screen flashes, and then when I go back to see if it set, it's not set to Beryl.

---

### Post by skyhopper88 on 2007-05-21
Run "beryl" from the terminal and see what error it spits out.

---

### Post by Trianth on 2007-05-21
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension



Using [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")
I got XGL working for a little while, but then my system crashed, and I still never figured out how to use Beryl, although I was able to set it as the window manager...

---

### Post by Goombie on 2007-05-22
What sort of video card do you have? It's a possibility that incorrectly installed drivers for that are mucking up Beryl.

---

