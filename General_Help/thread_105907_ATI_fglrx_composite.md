---
title: "ATI fglrx composite"
date: 2005-12-19
forum: General Help
---

### Post by Cybercool on 2005-12-19
Hello,

I want to know what possible and what not, and how to set it.
In the forum there are more questions abount this and not really answered.

So i ask here, and hope that there can be put up a good answer for everybody.

What is possible with the ATI fglrx driver with xcompmgr and composite.
Can you transparancy, shadow, windows acceleration?

And how to set it, when you set composite in youre xorg, it loads the mesa drivers.
And we don't want that of course.

Who can help, and explain how to set it up, and what works and what doesn't.

I hope that ATI comes with more support soon with this.
Windows Vista is problaby also going to work with this system so why not!!

---

### Post by simius on 2005-12-19
Ati does not support the Composite extension, so if you set it you won't get 3D acceleration indeed. From what I've heard Ati is not going to support Composite as it's still experimental, but that may change in the new version of X.org.

edit: It seems that Composite will be available for Radeon 9520 and below, using the unofficial radeon driver.

---

### Post by Cybercool on 2005-12-19
[QUOTE=simius]Ati does not support the Composite extension, so if you set it you won't get 3D acceleration indeed. From what I've heard Ati is not going to support Composite as it's still experimental, but that may change in the new version of X.org.[/QUOTE]


But can i create transparancy.
I don't want the fake transparancy from the terminal windows.
When you have a windows behind the terminal, you don't see it.
You only see the background.

---

### Post by Cybercool on 2005-12-20
Hello?

Does anybody has an answer about that?

---

### Post by Cybercool on 2005-12-21
Is there nobody who knowes how to make real transparncy in gnome with ati card?
Or is this impossible?

---

