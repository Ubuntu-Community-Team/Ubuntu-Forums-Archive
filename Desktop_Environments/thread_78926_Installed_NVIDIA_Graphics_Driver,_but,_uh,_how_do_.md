---
title: "Installed NVIDIA Graphics Driver, but, uh, how do you know it worked?"
date: 2005-10-19
forum: Desktop Environments
---

### Post by ivanjs on 2005-10-19
Just used the ubuntu guide's [ "How To INstall Graphics Driver (NVIDIA)"](http://ubuntuguide.org/#installnvidiadriver) and everything went okay, even managed to turn off the nvidia logo which flashes on for a millisecond when I restart X, but I don't see any new NVIDIA config menu selections or anything relating to NVIDIA. Should I be seeing something different to know that it installed properly?

Using a e-VGA GeForce 6200 PCI xpress card

---

### Post by ChrisTheGeek on 2005-10-19
If you saw the logo then it was installed fine.

A quick way to test it is to run one of the GL??? screensavers.  If they run smoothly then you're good to go.

If you want, you can add a menu item to the Applications menu to launch the nvidia settings program but I think the default settings will suit most people so this probably isn't necessary unless you like to play with these things.

---

### Post by GeneralZod on 2005-10-19
No, nothing shows up in the menus, although I gather there is some kind of nvidia GUI tool in the repositories somewhere (search Synaptic for "nvidia" - you'll know it when you see it :)).

Type "glxinfo" at a command-prompt; you should see the string

```

Direct Rendering: Yes

```

somewhere, although the fact that you had the nvidia logo show up is strong evidence that it is working.

---

### Post by The Headhunter on 2005-10-19
Run a graphical screensaver like Atlantis.  If it isn't choppy, then you know it worked.

---

### Post by djjuice on 2005-10-19
if you don't see the settings just go to the terminal and:
sudo apt-get install nvidia-settings

your probably missing that.. also like the other recommendations just run an opengl game or screensaver

---

### Post by ivanjs on 2005-10-19
Thanks, guys-all great suggestions. It definitely is working. Appreciate the help.

---

### Post by Mandor on 2005-10-20
Hello, I compiled a k7 kernel for my box (according to the HOWTO in this section) taking all defaults and after that installed nvidia drivers following the guide. On GL screen savers it says "No preview available" and the scrensaver does not run. "glxinfo" command gives me the following ouput:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

I suppose that is not quite OK :) I also have "Nvidia settings" link in gnome menu, but there are no settings actuallu there.

Any advisce will be appreciated. Thanks in advance.

---

### Post by gary79 on 2005-10-23
> Hello, I compiled a k7 kernel for my box (according to the HOWTO in this section) taking all defaults and after that installed nvidia drivers following the guide. On GL screen savers it says "No preview available" and the scrensaver does not run. "glxinfo" command gives me the following ouput:

name of display: :0.0
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x21 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x22 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
Segmentation fault

I suppose that is not quite OK I also have "Nvidia settings" link in gnome menu, but there are no settings actuallu there.

Any advisce will be appreciated. Thanks in advance.

I'm also in the same boat, K7 kernel and followed same guide with same out put from glxinfo.

---

### Post by Sutekh on 2005-10-23
Hey Mandor and gary79 I had *exactly* the same problem as you both with the k7 kernel and the nvidia drivers.  'glxinfo' gave a seg fault and nvidia settings had no settings to speak of.  I found that installing the nvidia drivers *before* installing the k7 kernel worked for me.  

I'm afraid I don't know why that worked though.

---

### Post by Visceral Monkey on 2005-10-24
Ok, I'm having the same issue with the k7 kernel. So how do I get this to work if i've already installed the k7 kernel?

---

### Post by Sutekh on 2005-10-24
You should check this out and see if it helps..
[Ubuntu FAQ]("http://www.ubuntulinux.org/support/documentation/faq/faqsection_view?section=Using%20Ubuntu")
Look down the page for the section on experiencing problems with official NVIDIA drivers.  Its for Hoary, but should work for Breezy.  I didn't follow this, I only just found it.

Check this thread too [HOWTO Install NVIDIA Drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

The very first things I did when getting my system up, were to install the k7-smp kernel and then the NVIDIA drivers.  When that didn't work, I re-installed everything (bad Windows habit), and installed the NVIDIA drivers first then the k7-smp kernel.  If you've got nothing to lose, maybe try that, but I wouldn't if you have everything setup and have lots of data.

Otherwise, can you still boot into the default 386 kernel? If so, do so and re-install the NVIDIA drivers from there.  Check to make sure that they are working.  If things are working there then boot into the k7 kernel and check again.

Unfortunately I don't really know why this error is happening, so if you can, wait and see if someone who knows more can help out.

---

### Post by Bannet on 2005-10-27
When I installed ubutu it installed i386 kernal my box is athlon xp 2900.
I installed the k7 kernal but when I installed the nvidia driver it downloaded the i386 complete kernal and thats why nvidia didnt work.I removed the nvidia driver installed the complete k7 removed the i386 kernal and installed nvidia and it worked.

---

### Post by ippiraman on 2005-10-27
I had this issue when I switched to the -686 kernel. My workaround for this was to run sudo nvidia-glx-config enable again. Then edit the /etc/X11/xorg.conf and change the driver "nv" to "nvidia".

And btw, i don't know if there is a restricted-module package for -k7, if there is then install it as well.


HTH

---

