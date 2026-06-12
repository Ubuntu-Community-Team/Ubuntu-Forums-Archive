---
title: "ATI graphics no longer accelerated... data provided."
date: 2006-09-24
forum: Desktop Environments
---

### Post by mjpatey on 2006-09-24
Something I did must have messed with my fglrx driver.  Google Earth is now painfully slow, completely unusable.  Even simple things like Google videos are looking really choppy.

I ran glxgears and only got 57 FPS (I usually get thousands of FPS), and no animation actually displayed, just a static image of the gears, and they even looked a little jagged.

Popular 3-D accelerated games are running at about 1 frame every 2 seconds!  I just tried Neverball and Neverputt, and it was like watching a slideshow, even in the menus.

I ran fglrxinfo, and got:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Are there any other places I need to check?  I looked in my xorg.conf file, and the fglrx driver appears where it should.

Thanks for any help you may be able to provide!

-Mark

---

### Post by pay on 2006-09-25
Did you upgrade the kernel? If you upgraded the kernel you have to reinstall the kernel modules.```
sudo rm /usr/src/fglrx-kernel*.debsudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

---

### Post by WalmartSniperLX on 2006-09-25
dude if it worked before, log out, and at the login menu (xserver) click reload xserver or something like that. Then try fglrxinfo again

as far as kernel upgrading, you need to reinstall to that kernel

---

### Post by mjpatey on 2006-09-25
I'm not sure if I upgraded the kernel or not.  I did re-run Automatix.  Does that upgrade the kernel?

And, if it turns out I didn't update the kernel, would it still be OK to run the code you listed, or would that screw things up royally?

Thanks!

-Mark

---

### Post by cneil on 2006-09-25
Thanks. This helped me out.  I didn't realize that I had to reinstall kernel modules every time I upgraded the kernel.

I had the same problem as mjpatey, but I used pay's solution to fix it.

---

### Post by pay on 2006-09-25
I don't think that Automatix upgrades the kernel. I don't think that it would stuff anything up if you re-run the commands.

---

### Post by mjpatey on 2006-09-25
Hmm... I tried running those commands, but got errors on every one.  It seems in each case, whatever files the command refers to didn't exist.

Here's what I got for the first line:

```
$ sudo rm /usr/src/fglrx-kernel*.debsudo module-assistant prepare
Password:
rm: cannot remove `/usr/src/fglrx-kernel*.debsudo': No such file or directory
rm: cannot remove `module-assistant': No such file or directory
rm: cannot remove `prepare': No such file or directory

```

Then when trying to build fglrx, it said that Kernel headers don't exist for it... and the rest obviously gave similar errors.

Do I need to reinstall something?

---

### Post by pay on 2006-09-25
thats okay if you get errors for "sudo rm /usr/src/fglrx-kernel*.deb". To install the headers type```
sudo aptitude install linux-headers-$(uname -r)
```

---

