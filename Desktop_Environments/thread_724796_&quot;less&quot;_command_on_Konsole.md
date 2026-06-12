---
title: "&quot;less&quot; command on Konsole"
date: 2008-03-15
forum: Desktop Environments
---

### Post by deepclutch on 2008-03-15
Hi,
In **konsole**,we cannot scroll through the output of "**less**" command.same goes with xterm also.
what I meant is for eg: 
```
less /etc/group
```
^here we cannot scroll with **mouse wheel** through the file.

But in gnome-terminal,everything works fine.I can scroll through the output.what is missing in konsole:confused:
yes,I DONT want to install gnome-terminal on this kde box. :)

---

### Post by der_joachim on 2008-03-15
That is strange behaviour indeed. Less has its own buttons for paging up and down: **w/B] and [B] z/B]. When reading a file with less, press the [B]h **key for more nifty help.

if you prefer using your scroll wheel anyway, use cat instead of less. cat will dump the entire contents of a file to stdout (your screen).

---

### Post by deepclutch on 2008-03-15
yes,I am using cat o/p to scroll via mouse.I have filed in konsole wish list:
[https://bugs.kde.org/show_bug.cgi?id=159340](https://bugs.kde.org/show_bug.cgi?id=159340)
How can I map above things in konsole :?

But,the weirdest thing is,In Konsole vim and nano allows scrolling with mouse wheel!

---

### Post by der_joachim on 2008-03-16
The most obvieus solution would be the shortcut menu in Menu >> Settings >> Configure Shortcuts. I did not find anything in these shortcuts which matches what you would like. This would call for some creative googling, or maybe trying alternative terminal emulators like the old xterm or rxvt. I do not know though whether they support mouse wheel paging.

---

### Post by deepclutch on 2008-03-16
even xterm doesnot support scrolling with mousewheel. :-|
only gnome-terminal does!

---

