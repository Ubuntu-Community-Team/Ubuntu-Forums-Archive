---
title: "Compiz does not work anymore"
date: 2007-12-12
forum: Desktop Effects &amp; Customization
---

### Post by Melcar on 2007-12-12
Compiz stopped working all of a sudden.  I just upgraded drivers, which are working fine by the way.  This is what I get when I try to run it from the terminal:
> 
principe@magicbox:~$ compiz SKIP_CHECKS=yes
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 1002:7244 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: line 378: /usr/local/bin/compiz: No such file or directory



Any ideas?  Already tried doing a clean install of all Compiz related packages.  fglrx is also whitelisted in /usr/bin/compiz.

---

### Post by Chris Riley on 2007-12-13
Not a response, but I too am having problems with compiz. 

I'm running Ubuntu Studio on top of Gutsy for AMD64, graphics driver is fglrx which is reported as active and in use.

When I try to activate enhanced desktop effects, I'm told that the composite extension is not available. When I run Control Panel, none of the desktop effects are present.

Please can someone tell me how to activate compiz?

Chris

---

### Post by Posterus on 2007-12-13
chris, I think your problem is that you dont have the compiz manager installed, try installing that and see if that helps, Melcar...try pressing alt+F2, this will bring up and command window that will let you enter one command as if you were in the terminal but it does not stay open like the terminal does, and then type in compiz --replace.  this will stop what ever your computer is using for visual affects and use compiz affects.

also i'd like to remind the both of you to NOT run commands in linux with out knowing exactly what they do, there are very dangerous commands people may try to tell you to use (this is not one of them) so always just simply try googling the commands first.

---

### Post by Chris Riley on 2007-12-13
Thanks for your response, Posterus. Unfortunately it isn't the lack of compis manager causing the problem.

I have an ATI Radeon X1250 chipset on my Asus AMD motherboard, and therefore I've got fglrx as the driver. It isn't working. When I use the Test facility in Screens & Graphics, the test fails and suggests I check my config.

Is there a conflict with this driver?:confused:

---

### Post by Chris Riley on 2007-12-13
This is not the solution to the original problem, but it may help.

I solved my particular problem by installing xserver-xgl. This allows the fglrx driver to work with compiz.

Thanks for the pointers.

Chris:)

---

### Post by DarKnyht on 2007-12-17
Thanks for the suggestions.  I am attempting to get Compiz to work on my very old presario with a S3 Twister-K card.

---

### Post by ajie on 2008-02-15
I am using hp pavilion with Twister K video card and Ubuntu 7.10. I cannot get compiz to work (or so I suspect). I can not change the visual effects to Normal (it is set to None by default), and I get the error message desktop effects could not be enabled. Can anyone help me?

---

