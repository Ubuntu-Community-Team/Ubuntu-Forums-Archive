---
title: "[SOLVED] CTL+Alt+F1 no longer working"
date: 2008-01-14
forum: Desktop Effects &amp; Customization
---

### Post by johnwren on 2008-01-14
This post may be in the wrong forum, for which I apologize. Thanks to this forum, and forlong,  I have compiz working nicelywith gutsy on a Dell Latitude D531 (fglx proprietary ati driver), and my next step is to try to use an external lcd project for a presentation next week.  My first attempt at the projector failed, and I noticed that CTL+ALT+F1 (Fn) does not bring up a terminal mode login screen -- as it does on my other (non-laptop) ubuntu systems.  Before I get working on the lcd projector problem, does anyone know how to debug and/or fix the terminal logins? [I did notice a thread dealing with an nvidia driver that suggested adding "vga=791" to the grub bootstring, but I suspect that is a rather complicated answer to the question.]
Thanks
As a ps, if anyone knows a good thread dealing with laptops and lcd projectors, particularly one with the ati driver under gutsy, I'd love to read id.

---

### Post by AndyCooll on 2008-01-14
The CTRL+ALT+F1 can be solved by enabling the function in your Keyboard Shortcuts (System > Preferences > Keyboard Shortcuts). There's a list of commonly used shortcuts and it may be that the one you want isn't currently configured.

:cool:

---

### Post by Forlong on 2008-01-14
Sounds like a framebuffer problem.

Try this:

First make sure to load the proper modules:
```
sudo gedit /etc/initramfs-tools/modules
```
Add this to the end of the file:
```
fbcon
vesafb
vga16fb
```
Save.

Then "unblacklist" them: ```
sudo gedit /etc/modprobe.d/blacklist-framebuffer
```
Put a # in front of```
 blacklist vesafb
```
and
```
blacklist vga16fb
```
Save.

Finally ```
sudo update-initramfs -u
```
Then reboot and see if it worked.

---

### Post by johnwren on 2008-01-14
Thanks to both forlong and andycool for their quick response.  The key shortcut CTL+ALT+F1 (Fn) does not show in the admin-keyboard shortcuts selection menu on any ubuntu system I have.  I suspect this functionality is much deeper in the kernel, and not at the level of gnome at all.  I also made active the frame buffer changes (fbcon, vesafb and vga16fb) and rebooted, but the problem is the same.  What I notice is that during startup, all other ubuntu systems I have seen write some visible messages to the monitor during the startup process.  These are all missing in my system.  Once I start the boot from grub, nothing happens on the screen at all until the username-password login screen -- which I think is part of the Xorg/Gnome stuff.  This makes me suspect something deeper is wrong, and that perhaps this thread is in the wrong forum -- but I really don't know where it belongs.  I also suspect (hope actually) that this explains why I seem unable to get the external vga connector on the laptop to work.  Many threads have suggested that rebooting with the lcd projector plugged in should get it to work -- but it remains stubbornly blank.  Again, I really appreciate any help or suggestions.  If nothing else works, I will do a clean install and start checking using the lcd projector from the very first -- before any other changes.  I will make a presentation to an international conference a week from today, and would really like to do it from ubuntu.  Of course, I don't want to make a fool of myself, and the presentation is more important than the operating system used to deliver it.

Any suggestions?

---

### Post by Forlong on 2008-01-15
Try installing **startupmanager** and setting the correct resolution with it.

---

### Post by johnwren on 2008-01-16
Thanks again forlong.  I adjusted the startup string using startupmanager, and notice that it put vga=791 in the bootstring of grub.  Now when I start I see the ubuntu 'splash' screen (which I did not see before) and the horizontal bar graph showing the status of the bootup process.  It's much better than a blank screen.  Unfortunately the CTL-ALT-F1 problem, and and inability to use an external lcd projector are still with me.  

I have since done a complete fresh install, and know that both features I want work when running off of the live CD before starting the install (Ie you can bring up a terminal screen by CTL-ALT-F1 and then go back to the gnome/xorg session by CTL-ALT-F7, and (on my Dell latitude D531 laptop) the Fn-F combination (shown on the keyboard as CRT/LCD) acts as a toggle between the laptop screen and the external lcd projector  However, once the install is done, this functionality is lost.

For me, the important issue is the lcd projector.  Does anyone know what exactly the 'screens and graphics preferences' tool does in administration?  I suspect if there is an answer, it is somewhere in there.

Again, thanks for the help, and any further suggestions from anyone are most welcome.

---

### Post by bruce.hobson on 2008-01-17
CTL+Alt+F1 no longer working or Black Screen on Boot until Login Screen.
Ubuntu 7.1 on a HP Laptop DV9225us

First make sure to load the proper modules:
Code:

      sudo gedit /etc/initramfs-tools/modules

Add this to the end of the file:
Code:

      nvidiafb
      vfbcon
      vesafb
      vga16fb

Save.

Then "unblacklist" them: 
Code:

      sudo gedit /etc/modprobe.d/blacklist-framebuffer

Put a # in front of Code:

      #blacklist nvidiafb
      #blacklist vesafb
      #blacklist vfb
      #blacklist vga16fb

Save.

Then update your ramfs 
Code:

      sudo update-initramfs -u

Finally edit your grub configuration file:
Code:
	
      gksudo gedit /boot/grub/menu.lst

Put or Change the following option(s) on your kernel lines:
	
      nosplash 
      vga=xxx

Bruce.Hobson

---

### Post by bruce.hobson on 2008-01-18
It looks like nvidiafb was not needed. Orignal post was correct.

Sorry about that!

My HP DV9225us is now working correctly with vga=792

Thank you very much.

Bruce Hobson

---

### Post by johnwren on 2008-01-18
Bruce,
Thank you for that.  I will try in the morning when I am fresh

---

### Post by johnwren on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramf](https://bugs.launchpad.net/ubuntu/+source/initramf) s-tools/+bug/129910  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Researching a bit further, this is related to launchpad bug 129910, and there is a thread with useful information at : [http://ubuntuforums.org/showthread.php?t=454392&page=3](http://ubuntuforums.org/showthread.php?t=454392&page=3)

Thanks again to Bruce Hobson who directed my attention to this.  Once I remembered the correct name for this, which is "virtual consoles" a lot more information popped up.  I will look at the way a working ubuntu 7.10 system (AMD64) is working, then make the suggested fix and report back.

---

### Post by johnwren on 2008-01-18
It certainly looked to me that the fix suggested above should have worked, but it did not.  I note that this problem is probably to be fixed in hardy heron, and I am content to wait until then.  It's not a huge issue, and I know I can get access to the console by booting the 'recovery mode' from grub -- in case xorg/gnome goes all funny.  I will now try to understand why I cannot connect an lcd project to the vga port on the laptop (although a connection using s-video works)  I think I may have to play with aticonfig -- which is why I wanted sure access to a console in case something goes wrong with X.  Any ideas on this problem are most welcome.

Thanks everybody for their help on this issue.

---

### Post by johnwren on 2008-01-19
A curious update to this thread.  My primary objective is to get the laptop working with an external lcd projector for a presentation this coming week.  After I tried the changes suggested by bruce hobson, and backed up by a bit of research (see above postings), I can now connect another lcd display to the vga port if it is on when the system is booted.  Fn-F8 (the Dell CRT/LCD switch combination on my laptop) is still ineffective, but it looks like I can now boot the system with an lcd projector installed on the vga port and use it.  I am at home, and without an lcd projector to test, but will confirm this when I get to work on Monday.  Many thanks to all who have helped on this forum.  It appears that I have two work-arounds to my problem with the lcd project (S-video also works) and the presentation will go ahead under ubuntu as planned.  I've also posted on the Dell and Phoronix-ati forums, and on the hardware/laptop formum here, and will post a note on those forums as well.

---

### Post by bruce.hobson on 2008-01-20
On another computer of mine. I discovered that it needed a new module to work correctly. fbcon

If your system is still not working correctly try fbcon with above Re: CTL+Alt+F1 no longer working

Bruce

---

### Post by johnwren on 2008-01-22
Bruce,
   Thank you again!  fbcon did the trick.  After my presentation I'll try to back out the other changes one-by-one, and see which one(s) are necessary for the Dell Latitude D351.  I'm going to mark this thread solved.
John

---

### Post by r0ydster on 2008-01-24
Is this going to be fixed in Hardy Heron ?

I've been using using Linux since 1997, and the framebuffer has always been enabled in every distro that I've ever run.  I was surprised that it had to be enabled.

MIke

---

