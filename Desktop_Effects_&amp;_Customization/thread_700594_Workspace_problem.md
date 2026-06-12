---
title: "Workspace problem"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by Midog on 2008-02-18
Hi All,
I'm completely new to Ubuntu. I literally researched everything I know about it yesterday, when I installed Ubuntu 7.10. I enabled the desktop effects and the desktop cube. It worked fine for a little while and then I couldn't rotate the cube or use control+alt+left/right, only alt+control+down. Please, someone help me fix this problem. :mad:

P.S. I researched everywhere for this problem and I can't seem to understand what it is still.

---

### Post by chavanak on 2008-02-18
First see if the desktop cube and rotate cube plugins are activated. Then make sure you have 4 desktops for the cube... I think this must solve your problem

---

### Post by Midog on 2008-02-18
I'm sorry, but it still didn't! Not only were they activated when it happened, it only switches workspaces when the desktop wall is enabled. And not only that, but after I rebooted, every time I enable them, it reverts back to extra instead of custom (I have compiz-fusion manager).:confused::(

---

### Post by chavanak on 2008-02-18
Which is Your graphics card
type in 
lspci | grep VGA

and post the output

Also type in 'compiz' (without quotes) in a terminal and post the output.

---

### Post by Midog on 2008-02-18
My VC (video card) is nVIDIA GeForce 6150 LE
{lspci | grep VGA}:
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0241 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (800x600) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by Midog on 2008-02-18
when i typed compiz, my pc froze for a second and then i couldn't use the keyboard, so i clicked "log off, switch user, etc." and then pressed alt+ctrl+backspace.

---

### Post by chavanak on 2008-02-18
remove the compiz config files and see if ti works. If not completely remove compiz from your synaptic and reinstall it again

---

### Post by Midog on 2008-02-18
ummm... how do i remove the config files. Please provide steps.

---

### Post by chavanak on 2008-02-18
[http://ubuntuforums.org/showthread.php?p=4323729](http://ubuntuforums.org/showthread.php?p=4323729)

see here

---

### Post by Midog on 2008-02-18
Man!!!!
It Still Doesn't Want To Work!

---

