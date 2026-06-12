---
title: "[SOLVED] Blank Gnome Terminal and Systems Monitor Windows"
date: 2008-12-27
forum: General Help
---

### Post by Quid on 2008-12-27
I have a weird problem that seems to effect only a couple of windows. 
 
My Gnome terminal, when invoked through the menu or run from the command line comes up blank. I am not sure if it is actually taking input. Configuring doesn't help.

On testing for additional issues - my System Monitor graph, which has always worked,  does the same thing. As does my startup screen for Unreal Tournament 2000. 

Other screens and even Unreal works fine Compis cubes spin and workspaces are good. Other effects seem fine - so I don't think it is the Nvidia driver - seems too specific. 

Could be my xorg.cfg ( I am at 173+) - but I can't seem to get the Nvidia settings applet to run in sudo to fix it without the terminal. Again, it seems way to specific.

I did reinstall the Gnome Terminal, and tried running from another user - same results. 

Any thoughts?   My daughter is waiting for me to install the DigiPro tablet I got her for Christmas, and I hate her thinking Windows would be better :confused:

In a (perhaps) unrelated issue my windows "frames" seem to be missing from windowpanes. Can't seem to get them back? Set up a session for Emerald etc. 

Thanks in Advance!
 Quid form Canada

---

### Post by Quid on 2008-12-30
Well situation solved...:D

I found this link:
[http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/](http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/)

wherein they state:
--------------------
window decorations have disappeared. This is a fairly common problem amongst systems using ATI or Nvidia video cards and commonly occurs after switching to a higher resolution. The fix is fairly simple.

Ubuntu Desktop effects - How to fix the missing titlebar:

   1. Open up a terminal and type sudo su (enter your password)
   2. Type gedit /etc/X11/xorg.conf
   3. From the xorg.conf file, find the section called Section "Device" and just before EndSection, add the following and save the file:

          Option "AddARGBVisuals" "True"
          Option "AddARGBGLXVisuals" "True"

-----------------
I am not sure why this works - but it fixed my windows decor and the Gnome Terminal Problem.... 

I hope this helps others! 

Quid:popcorn:

---

### Post by Cranakis on 2009-01-08
I am having the same terminal problem you are and I cannot figure out how I am supposed to enter the code to fix the problem without being able to use the terminal.  What am I missing?  Where do I type the above code?

---

### Post by Cranakis on 2009-01-09
Answered my own question.  I typed the commands in the terminal window and even though it was tough because i could not see what I was typing, the code ran fine and opened the gedit window which i could see fine.

---

