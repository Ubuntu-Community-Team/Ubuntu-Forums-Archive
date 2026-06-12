---
title: "Is it a known Ubuntu 13.10 bug where BACKSPACE no longer works in Nautilus (&quot;Files&quot;)?"
date: 2013-10-22
forum: Desktop Environments
---

### Post by Jim_Granite on 2013-10-22
On every other operating system I've ever used, including other Linux's, the keyboard BACKSPACE key conveniently moves up the menu hierarchy in the file browser.

Pressing the keyboard BACKSPACE key is fast, quick, and natural, especially when your hand is already on the keyboard moving a trackpoint or touchpad.

However, I just moved from RHEL6 to Ubuntu 13.10, and I'm shocked that there is a nasty bug where my BACKSPACE key no longer moves up one level in the hierarchy. When I'm in Nautilus (aka "Files"), pressing the keyboard BACKSPACE key does ... well ... um ... it does nothing.

Huh?
I'm shocked if this was missed in the testing for Ubuntu 13.10 - so - that's why I first ask if it's just on my system.
I'm not sure if this missing-backspace-key bug is specific to my laptop or to Ubuntu 13.10 in general.

Q: Does YOUR backspace button work (to go up one level in the hierarchy) in Nautilus?
If not, do you know how to fix or workaround this bug?
Or, is it a setting that was accidentally turned off somewhere in the Ubuntu 13.10 defaults?

Please advise, as it's absolutely unthinkable for the keyboard BACKSPACE key, which in all other operating systems on the planet moves up one level in the hierarchy when browsing graphically, to do nothing on my PC.
[ATTACH=CONFIG]247172[/ATTACH]
EDIT: Clicking around furiously, I found that the weird two-handed combination of alt and left arrow works, but, that's as crazy as not having a BACKSPACE button.
Is the missing BACKSPACE functionality bug just on my keyboard or is it on yours also?

---

### Post by mc4man on 2013-10-23
Gnome decided to go with alt+arrow keys so they don't consider this a bug, just a design decision
In most cases you can enable it by editing a local file
```
gedit .config/nautilus/accels
```

at the bottom add this (no ; like other entries
```
(gtk_accel_path "<Actions>/ShellActions/Up" "BackSpace")
```

kill nautilus with nautilus-q then open nautilus & ck. (or log out/in

---

### Post by Jim_Granite on 2013-10-24
> **mc4man said:**
> you can enable it by editing a local file

That worked perfectly!
```

$ vi ~/.config/nautilus/accels
ADD:
(gtk_accel_path "<Actions>/ShellActions/Up" "BackSpace")
$ sudo reboot

```

Now the backspace works in the file manager. 
Thank you for that suggestion; it's pure genius!

---

### Post by 3rdalbum on 2013-10-24
> **Jim_Granite said:**
> Please advise, as it's absolutely unthinkable for the keyboard BACKSPACE key, which in all other operating systems on the planet moves up one level in the hierarchy when browsing graphically, to do nothing on my PC.

It can't really be *that* unthinkable, mate... I never even knew that backspace went up a directory. On any operating system.

It's a Gnome decision not an Ubuntu one. It makes sense when you think about it - Backspace is used to delete things, so it's not very consistent as a navigational key.

---

### Post by Jim_Granite on 2013-10-24
> **3rdalbum said:**
> It can't really be *that* unthinkable, mate... I never even knew that backspace went up a directory. On any operating system.
<smile> Well, it's unthinkable to me! And, to [this guy]("http://itsfoss.com/seven-things-i-hate-in-ubuntu-13-04/") (who doesn't yet know the fantastic fix from **mc4man **above).
* [Seven Things I Hate In Ubuntu 13.04]("http://itsfoss.com/seven-things-i-hate-in-ubuntu-13-04/") *

> **3rdalbum said:**
> It's a Gnome decision not an Ubuntu one. It makes sense when you think about it - Backspace is used to delete things, so it's not very consistent as a navigational key.
Hmmm... I've been using the backspace key ever since I learned to type on a keyboard to "go back" one space. So, while I don't remember what decade it was that I learned that the backspace key went up in the hierarchy, but, ever since then, it's a natural and fast slap, to go up one level, slap-slap-slap to go up three levels of the hierarchy, etc.

Since I'm on dual boot Windows & Linux, having the backspace key do the same thing in both is what I've come to expect.

It may matter more to me that I don't use a mouse, so, my hand is always on the keyboard pushing that "erasure" in the middle of the keyboard. Dunno, but, not having the backspace key work right is as unthinkable as if they removed the zero key, and expected you to type "shift + o" instead. Sure, the alt + left arrow might work; but it's not what my "muscle memory" has been doing for about 3 decades and counting. 

There should be a list of "Ubuntu 13.10 annoyances & solutions" somewhere ... where we can add this wonderful solution from **mc4man.**

---

### Post by Jim_Granite on 2013-10-25
What's the best way to mark this solved thanks to your help?

---

### Post by BlinkinCat on 2013-10-25
> **Jim_Granite said:**
> What's the best way to mark this solved thanks to your help?

Hi Jim,

In the Thread Tools at top of page there is a drop down menu - select "Mark as Solved"

cheers - :)

---

### Post by Jim_Granite on 2013-10-25
> **BlinkinCat said:**
> Thread Tools
Aha! Thanks. I didn't see that before. 
It is now marked as solved.
Thank you for all the wonderful help.
Much appreciated.
I hope, in the future, I can pay this one forward!

---

### Post by ilja.polivanovas on 2013-12-15
Hi, I have exatly the same issue, but BACKSPACE key did not started wokring and the.config/nautilus/accels file somehow restores to the previous version after reboot. Ubuntu 13.10

Any other ideas?

---

