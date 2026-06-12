---
title: "Cannot start computer from after display offs."
date: 2008-07-02
forum: Desktop Environments
---

### Post by mirchichamu on 2008-07-02
I cannot start my laptop after the display sleeps. I have to shut down through shut down button and restart. This a big problem. Please help.

---

### Post by ProbablyX on 2008-07-02
Can you see the BIOS and the "Press Esc to launch GRUB menu"? Or is the entire computer not giving you anything?

---

### Post by mirchichamu on 2008-07-02
> **ProbablyX said:**
> Can you see the BIOS and the "Press Esc to launch GRUB menu"? Or is the entire computer not giving you anything?

Thanks ProbablyX for ur support,
No it is completely locked. Esc not working. I have to shut down by pressing the shutdown button.

---

### Post by ProbablyX on 2008-07-03
> **mirchichamu said:**
> Thanks ProbablyX for ur support,
No it is completely locked. Esc not working. I have to shut down by pressing the shutdown button.

Oh, so the computer boots and so but this occurs after the computer goes to sleep?

I can you use your PC before the computer goes to sleep?
If you can use the PC until the computer goes to sleep it might be a driver issue.

Do you know what make your graphics card is?
If not try this:
> 
lspci | grep VGA

That will post your graphics card.

Now run this:
> 
glxinfo | grep vendor


That will tell us about your graphics card driver.

Now can you post the output you got from those commands here?

---

### Post by mirchichamu on 2008-07-04
Thanks a lot for your interest to help me.

For the first command I got this: VGA Compatible Controller = ATI Technologies Inc RV 350 [ Mobility Radeon 9 600 M10]

The second command freeze my computer and I have to shut down my laptop and restart.

I think the problem is here in the driver of the display.
I shall be thankful for any solution.

---

### Post by ramaswamyps on 2008-07-04
try adding vesa to kernel line in grub/menu.lst
you can try booting in recovery kernel also.
it will regenerate xorg.conf

---

### Post by mirchichamu on 2008-07-04
> **ramaswamyps said:**
> try adding vesa to kernel line in grub/menu.lst
you can try booting in recovery kernel also.
it will regenerate xorg.conf

Thanks for ur support.
I am newbie to ubuntu. Will you please explain in simple words how to do what you have asked me to do?

Thanks in anticipation.

---

### Post by mirchichamu on 2008-07-05
My problem not yet solved.I need help please.

---

### Post by ramaswamyps on 2008-07-06
while booting at grub screen select recovery kernel and boot'
when it ask you to reconfigure Xserver do that.
your problem may be solved with that.

---

