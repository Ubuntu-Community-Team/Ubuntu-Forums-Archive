---
title: "How to setup GRUB Menu?"
date: 2009-05-22
forum: Desktop Environments
---

### Post by Linux_Coder on 2009-05-22
Hi.

I have ubuntu 8.04 and 9.04 installed on my system. And when I am starting computer, the huge menu appears:

[IMG]http://s40.radikal.ru/i088/0905/74/f47712352b18.jpg[/IMG]

All I need is 1 for 8.04 and for 9.04, other options should be disabled. If u know how to do this, please explain.
Thanks.

---

### Post by Chemical Imbalance on 2009-05-22
An easy to use GUI would be startup-manager

```
sudo aptitude install startup-manager
```

Or you could manually edit /boot/grub/menu.lst with gedit

```
gksudo gedit /boot/grub/menu.lst
```

You should read up on editing menu.lst first though if you take that route.  Could end in headaches if you mess up.

---

### Post by Minsky on 2009-05-22
The menu entries are normally located towards the end of **menu.lst**, usually after the line

 **## ## End Default Options ##**

Each menu entry consists of a block of 4 or 5 lines prefixed with the words **title**, **uuid**, **kernel**, **initrd** and **quiet**. Add a double hash **##** to the beginning of each line of the block corresponding to the menu entry that you wish to prevent from being displayed, including the blank line between the blocks and **Save**. I agree with CI though, I'd do some reading up if you're not too sure about editing Grub menus

---

### Post by Chemical Imbalance on 2009-05-23
Before anything, give startup-manager a try, then worry about manual editing if it doesn't suit you.

---

