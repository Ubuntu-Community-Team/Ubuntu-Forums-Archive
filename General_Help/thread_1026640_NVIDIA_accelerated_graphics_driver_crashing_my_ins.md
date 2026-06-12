---
title: "NVIDIA accelerated graphics driver crashing my installation"
date: 2008-12-31
forum: General Help
---

### Post by meself on 2008-12-31
hi.  i have a dual boot machine [Ubuntu8.04 and windowsXP] with a NVIDIA geforce mx200 graphics card.  the motherboard is an intel d865pearl.

when i attempt enable normal or extra visual effects under appearance preferances, i get prompted to install a NVIDIA restricted driver.  but when i do that, it freezes up my startup and displays a box that says "out of range" against a black screen when i attempt to start into Ubuntu, requireing a re-installation.

is there a work around for this?

---

### Post by Miles_Prower on 2008-12-31
yes, I just went through the same thing here:
[http://ubuntuforums.org/showthread.php?t=1026227](http://ubuntuforums.org/showthread.php?t=1026227)

Is your computer networked with ethernet cable or wirelessly? Is auto login enabled?

---

### Post by questioning on 2008-12-31
do you honestly think you have to reinstall your machine if you have a misconfigured driver? better stick with windows then.

---

### Post by meself on 2008-12-31
> **questioning said:**
> do you honestly think you have to reinstall your machine if you have a misconfigured driver? better stick with windows then.
ok questioning.  thank you for your encouragement.  i wish you the best as well.

---

### Post by Miles_Prower on 2008-12-31
did you try the fix from the other thread? The one where I had the same issue, not the one where I put a link to a 2,000 page thesis I wrote honoring "questioning" for his philanthropy and magnanimous demeanor. (I think I also compared him quite favorably to Richard Stallman).

/edit : the thesis was 2,000 words, not pages.

//edit: no, i had it right the first time, 2,000 pages.

---

### Post by questioning on 2008-12-31
prepare to be illuminated:

the real fix for that problem dwells deep within your xorg.conf

literally thousands of wiki pages on that topic just wait to be discovered

---

### Post by Miles_Prower on 2008-12-31
yes, yes, I covered your ability to solve problems without diagnosing them in my essay. Black paint is more illuminating.

The xorg.conf file (located here : /etc/X11/xorg.conf) is probably worth a look (didn't help me, but my problem was based on screen resolution), but purging and reinstalling the advanced graphics drivers definitely couldn't hurt.

---

### Post by meself on 2009-01-01
Thank you Miles Prower.  I don't think I want to change to an older kernel.  I will wait for a new release of the nvidia restricted driver or an Ubuntu update that allows enhanced graphics with the nvidia-glx-legacy open source driver.  i have now installed the open source enhanced driver "nvidia-glx-legacy" but it does not yet allow the normal or extra visual effects on the desktop.  that's really all i wanted it for in the first place.  hopefully there will be a bugfix from nvidia or ubuntu soon.

---

### Post by stderr on 2009-01-01
> **questioning said:**
> better stick with windows then.

Questioning: If you think that Windows is easier to use than Ubuntu, then maybe **you'd** better stick with Windows :cool: Let's face it, I think we've all re-installed Windows for problems which, had we been able to see into the pre-compiled binaries/libraries, would have been laughably basic.

meself: When you get problems launching the graphical user interface, you should normally be able to switch to a TTY with Ctrl + Alt + F1 (or F2, F3... to F6). There you can login and exec commands. You can then try to pull up the GUI once more by executing

```
startx
```

If you run into problems actually being able to switch to another TTY, you could boot in recovery mode (although I can't remember what you get by default with that), or use a Live CD or installation disk to get a terminal.

"Out of range"... hmm... looks like it might have autodetected the refresh rates wrong or something. I wonder if a 

```
dpkg-reconfigure xserver-xorg
```

would have helped. Also, posting your xorg.conf (with restricted drivers installed) might help us figure it out.

Also, did you try running 

```
nvidia-xconfig
```

although I never have high hopes with that.

---

### Post by pietjanjaap on 2009-01-01
Install envy, is inside of ubuntu.
Go to the envy website(google), there you can find the textmode instructions.
To start envy in textmode sudo envyng -t, then you get a menu in textmode.
Choose remove drivers, (the ubuntu will start again without drivers if you want).
Now reboot to recovery mode,
choose x fix (here your video card and monitor will be search.
then go to textmode,
install your driver with sudo envyng -t
reboot.
If your screen size is not ok, go to system-preferences-screen resolution, and change it, and reboot.

If you install the video driver with envy with gui, then you can choose 3 drivers(nvidia).
If it goes wrong always remove everything and start from the beginning.


So if you get in problems, you can always remove your drivers, boot in ubuntu and work with grafics screens.

---

