---
title: "xserver-xgl / keyboard issue"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by OldGrey on 2007-10-22
Hi

I installed xserver-xgl and the visual effects worked fine. Unfortunately it changed my keyboard settings from standard UK to I think US. I checked the xorg.conf file and all the settings were correct.The only way to fix this was to uninstall xserver-xgl.

Is there a way of having the effects and my UK keyboard?

More detail. When I log in I get this :

"The X system keyboard settings differ from your current GNOME keyboard settings. 

Expected was model "pc101", layout "us" and no options, but the the following settings were found: model "pc105", layout "gb	basic" and no options. 

Which set would you like to use?"

I have tried sudo dpkg-reconfigure xserver-xorg to no effect. Presumably there is a file somewhere with this Xsystem keyboards settings, but I cannot track it down. Can anyone point me in the right direction?

---

### Post by in_flu_ence on 2007-10-23
Just exchange info with my thread ([http://ubuntuforums.org/showthread.php?t=588535](http://ubuntuforums.org/showthread.php?t=588535)). I actually don't have the problem when I had xserver-xgl but the problem arises after the uninstallation.

Not sure if it is actually a bug of ubuntu or gnome.

---

### Post by OldGrey on 2007-10-24
At least its nice to know I am not alone, even though there doesn't seem to be a solution as yet.

For interest I did not get the message when I had xserver-xgl, but because the UK keyboard is a different layout from US (symbols and punctuation are in different places) I noticed as soon as I tried typing. Getting rid of xserver-xgl solved that problem but I get the annoying message now.

---

### Post by nero666 on 2007-10-24
I'm having the same problem here!

Using Brazilian Portuguese Keyboard.

My mouse also doesn't work.

It happens only when i try to use XGL (ATI)

i'm using gutsy...

---

### Post by dogskull on 2007-10-24
I have the same problem on gutsy.  Unistalled xserver-xgl because it seemed to take too long to boot.  Still trying to straighten out the ATI issues.

There's a [solution posted at Launchpad]("https://bugs.launchpad.net/ubuntu/+bug/154401") that worked for me. (Except that mine showed up as "kbd.sysbackup".)  I logged out and back in and it was fine.  Also rebooted and was fine.

> 
 Magnus Hjorth wrote on 2007-10-23:

I discovered a way to get rid of this problem:
Open gconf-editor,
Browse to /desktop/gnome/peripherals/keyboard/xkb.sysbackup/
Unset both the keys in that 'folder' (or whatever you want to call it)


---

### Post by OldGrey on 2007-10-25
Thanks, I'll give this a try when I get home from work. 

Did so and it worked - thanks again

However this does not seem to address the real problem for me which is that installing xserver-xgl resets the keyboard to US 101 and you don't get the choice! I'll search launchpad to see if it has been picked up there.

No xserver-xgl - no wobbly windows!* 

This seems to be to most relevant launchpad entry:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/155284](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/155284)

*Temporarily given up on this on the grounds that all the important stuff seems to be working now.

---

### Post by in_flu_ence on 2007-10-25
anyway, the tweak works for me. Of course I guess that's the problem about having compiz by default in gutsy. Probably we should have an option.

---

