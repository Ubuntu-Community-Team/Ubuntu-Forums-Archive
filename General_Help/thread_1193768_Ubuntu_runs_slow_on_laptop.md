---
title: "Ubuntu runs slow on laptop?"
date: 2009-06-21
forum: General Help
---

### Post by nasachusetts on 2009-06-21
I installed Ubuntu on an IBM Thinkpad with these specs
ProcessorIntel(R) Pentium(R) M processor 1600MHz Memory1026MB (266MB used)
Display Resolution1400x1050 pixels OpenGL RendererMesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL X11 VendorThe X.Org Foundation

It works but it runs slow even with all of the visual effects turned off.  According to the minimal requirements from Ubuntu, I thought it would handle Ubuntu with no problem.  It doesn't bother me until I start using the scroll bar in applications and even large webpages when it just creeps instead of scrolling smoothly.  Is there someway to make it run faster or should I try a different distro?  Would anybody have any recommendations here?

---

### Post by nandemonai on 2009-06-21
Intel graphics by chance?

---

### Post by wpshooter on 2009-06-21
Is the video card on this machine "SHARING" system memory/RAM ?

If it is, then see if you can go into BIOS and adjust the amount of system memory that is shared with the video and adjust the amount either up or down to see if that will make a difference in performance.

---

### Post by nasachusetts on 2009-06-23
The video card is an ATI mobile 9000.  I'm not sure if the system is sharing memory but I went into bios and couldn't find any option for that.  It doesn't seem like this laptop shouldn't be able to handle it when XP runs fast, but I really don't want to have to run Windows on it.  Is there any other distro that is similar to Ubuntu in terms of being easy to use?

---

### Post by del_diablo on 2009-06-23
The GPU just happen to lack a driver.

---

### Post by nasachusetts on 2009-06-23
Is there somewhere I might find a driver to work with this?

---

### Post by nasachusetts on 2009-06-23
After looking around on google for some answers here, I am convinced that it is the video card that is the culprit of the slowness.  Anyone know of a driver that still supports this old card?

---

### Post by synapsys on 2009-06-23
Maybe here?

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by nasachusetts on 2009-06-23
Looks like they don't support this card anymore from that link.  I think I might try Linux Mint from seeing a few people with the similar problem had success.

---

### Post by synapsys on 2009-06-23
If it works on Mint then there is definately a way to get it working on Ubuntu.

Maybe it's not the driver after all....

[http://ohioloco.ubuntuforums.org/showthread.php?p=7503059](http://ohioloco.ubuntuforums.org/showthread.php?p=7503059)
(go from bottom to top)

---

### Post by nasachusetts on 2009-06-25
That actually did the trick and everything works wonderfully now.  Thanks for finding that link it saved me a headache of installing different distros.  CPU idles at about 10-15% now and the larger webpages on firefox scroll much more faster.  Thanks again!

---

