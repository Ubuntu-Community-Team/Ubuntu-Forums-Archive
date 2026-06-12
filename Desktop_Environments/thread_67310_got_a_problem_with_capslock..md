---
title: "got a problem with capslock."
date: 2005-09-19
forum: Desktop Environments
---

### Post by transpot on 2005-09-19
I have a weird problem with keys.

In a console, When I type 'abcdefghi" with capslock turned on, It displays "ABcDeFGHI" instead of "ABCDEFGHI". yeah.. strangely letter c and e are typed as lower cases. So I have to press shift to type the upper case letters. In X-window's terminal, I don't have that problem. My ubuntu is running on Virtual PC 2004 in XP, but I don't think that's the cause.. hmmm can anyone help me out?

---

### Post by Xian on 2005-09-19
What type of keyboard did you select during installation?
You may need to reconfigure this.

$ sudo dpkg-reconfigure xserver-xorg

---

### Post by transpot on 2005-09-19
[QUOTE=Xian]What type of keyboard did you select during installation?
You may need to reconfigure this.

$ sudo dpkg-reconfigure xserver-xorg[/QUOTE]

I tried that.. but no luck. The keyboard was set to U.S English 104.
I have no problem typing uppercase 'e' and 'c' in GUI mode. but I get this strange behavior in the text consoles. I don't know why this happens

---

