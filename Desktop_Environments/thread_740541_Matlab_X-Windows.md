---
title: "Matlab X-Windows"
date: 2008-03-30
forum: Desktop Environments
---

### Post by JohnWilliams on 2008-03-30
Hello,

I am attempting to run Matlab remotely using X-Windows.  My machine is a dell dimension 2400 and running the latest version of ubuntu.  The problem is from my end, as I have had no problems forwarding X-windows Matlab GUI to other machines from this particular matlab server.

The issue is that x-windows does indeed forward the gui but I can only see the command window.  The tool bars, editor, etc are all a blank-white screen, that can be accessed, but not viewed, i.e. if I place and click the mouse at the appropriate position i get the desired response, just can't see these areas of the gui.

All other programs, firefox etc work perfectly with x-windows.  Any ideas would be greatly appreciated.  And apologies in advance if this isn't the right forum,

John

---

### Post by aroch1 on 2008-04-01
I've been using matlab in this manner for about two years and have not been able to resolve the same exact problem!  I hope a solution pops up!!!

---

### Post by xrat on 2008-05-10
Same problem here. And it seems to affect more than just MATLAB. I found that also Maple and Mathematica do not work. Maple shows the exact same empty/white windows. Mathematica shows more but also, it seems, 1 additional empty window which even cannot be closed. :confused:

-- xrat

---

### Post by xrat on 2008-05-10
@JohnWilliams and @aroch1: Did you check whether the problems persist after switching System > Preferences > Appearance > Visual Effects to "None"? In case of MATLAB and Maple on my machines it seems to be related to compiz, ie. Visual Effects set to at least "Normal". Both programs start up correctly when Visual Effects are off.

Mathematica has different problems which are tracked well in [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197163](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197163)

HTH,
-- xrat

---

### Post by Whiffle on 2008-05-10
Try ssh -Y instead of ssh -X .  It relaxes the security a bit but makes matlab work if i remember right.

---

### Post by muadnu on 2008-05-13
I'm seeing the same, in Hardy 64 bit. I just tried the ssh -Y fix, but it doesn't help. By the way, I just tried to run Matlab remotely in Arch, and it works perfectly.

About Mathematica, the problem lies, at least in my case, in lacking the right Mathematica fonts, but I haven't found them anywhere.

---

### Post by jwsohn on 2008-05-17
Xmanager provides mathematica fonts as a separate package but this is for Windows. Check [http://www.netsarang.com/download/main.html](http://www.netsarang.com/download/main.html). You might be able to extract the font file. 

I am having the same problem for Matlab as well. I'm using matlab -nojvm option for a workaround.

---

