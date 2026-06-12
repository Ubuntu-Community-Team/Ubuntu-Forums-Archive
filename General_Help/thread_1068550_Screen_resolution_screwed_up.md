---
title: "Screen resolution screwed up"
date: 2009-02-13
forum: General Help
---

### Post by dbyjazz on 2009-02-13
I just installed Ubuntu on my XP laptop, well I cant see the whole screen. So I go in to change the screen resolution and my creen gets all messed up with lines going accross the screen. Is there any way to fix this? I have to reinstall Ubuntu just to fix the lines.
       
Thanks

Oh ya I have to use my phone to do this, so the sooner someone can help me the better :)

---

### Post by Peter09 on 2009-02-13
when booting (before the grub prompt), hit the escape key and the select recovery mode. When the menu comes up select the option to fix the xserver.

---

### Post by dbyjazz on 2009-02-13
I dont see that option. When exactly do you hit esc.?

---

### Post by dbyjazz on 2009-02-13
Nevermind. That didn't work

---

### Post by stalkingwolf on 2009-02-13
> I dont see that option. When exactly do you hit esc.?

When Grub first starts.  It will then bring a boot menu up.  Select
recovery mode.  After recovery runs a window will come up giving you several options, two of which are "fix broken packages" and "fix X server".

I would first select  "fix broken packages" when that is finished ( it will
tell you finished, then select the fix X option. again it will tell you it is finished.  Then reboot.  If that does not fix your issue, open a terminal
and enter

```
sudo displayconfig-gtk
```  under model try setting it to
Generic  on the left and what ever your native display and resolution are on the right.

you can also try setting it under driver to your display adapter or other and Vesa.

---

### Post by dbyjazz on 2009-02-13
thanks I'll give it a shot

Im a real noob, how do I open up a terminal? Hopefuly it's not after the log in because once i log in i cant see anything

---

### Post by Peter09 on 2009-02-13
You do not need to open a terminal in recovery mode, you'll get a menu for these things.

---

### Post by dbyjazz on 2009-02-16
What?

---

