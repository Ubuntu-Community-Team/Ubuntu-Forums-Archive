---
title: "Gutsy on a Dimension  XPS 400 - ATI issues"
date: 2007-11-09
forum: Dell  Ubuntu Support
---

### Post by redwarrior on 2007-11-09
Hello everyone.  I am a newcomer to Ubuntu, although I've used linux before in the past (although that was redhat and I'm incredibly rusty).  I've read through some other threads, but I don't think I've found one yet that is an exact match to the problem I'm having.

I installed gutsy on my Dell Dimension XPS 400 desktop last night to a spare hard drive that was blank.  Everything went incredibly smoothly after the install finished and I rebooted.  After running the usual update packages, it came up with an error regarding a restricted driver for my ATI video card.  (I will find out the exact model of video card and post it here tonight.)  Although the display looked fine, being the visual person I am, I decided to give my video over to ATI and see what happened.  Everything seemed to go fine...until the necessary reboot.

Now upon booting, I get the error that the "video mode 2 is not supported" and nothing but a black screen.  I can't even get to a command prompt.  Once the system gets past post, poof!  Now, coming from a Microsoft (please don't hurl things...we all make mistakes!;) ) background, normally in these circumstances, I would boot to safe mode, get rid of the offensive driver, and life would be good again.  Here, though, I'm at a loss as to how to proceed to recover my install.  Luckily, I did this on a spare hard drive and I still have XP running fine on my other hard drive, so I can get any system info or driver files I need from there.

One other question, kind souls!  When I installed gutsy to the second hard drive I eventually planned on using the system as a dual boot (after I get another SATA cable) since I have to run XP.  (I'm a windows administrator hoping to defect.)  Is this something I can do after the fact or will I end up needing to reinstall in order to get the appropriate files in the MBR on the primary drive?

Thanks for your patience in helping me with my jailbreak from MS!
redwarrior

[-o<

Update - It is a radeon card...I'm looking through the forums now, but pretty much all posts I see assume you can still at least see a command line.  All I see is blackness.  I can hear what's going on, but can't see anything.  Evil, evil ATI!

---

### Post by redwarrior on 2007-11-09
Ok, I did answer my own question about Ubuntu "safe mode" by stopping grub before the boot sequence began, so I'm off to find some posts with the command-line operations for making this sucker work.

My card is listed as a "ATI Radeon X300/X550/X1050 Series" and the error I get on boot after grub and the first graphical Ubuntu screen (basically right when it loads the ATI driver) is "2: Digital Input Cannot Display This Video Mode".  I'm off to go searching, but if anyone has dealt with this before and can point me in the right direction, they will earn my eternal gratitude.  I can't wait to get playing with my new install!

---

### Post by redwarrior on 2007-11-09
I am back again.  I guess I should thank ATI because I am learning a lot from this issue.  :-D  Sometimes the best way to learn is by having to fix something you have messed up.

In any case, I have been working on the tips shown in the BinaryDriverHowto/ATI thread.  I did find some fixes I could make, but I'm still getting the same error.  I examined the xorg log at /var/log/xorg.0.log and found just the following errors:

AIGLX ERROR: dlsym for __driCreateNewScreen_20050727 FAILED (/usr/lib/dri?$
AIGLX: reverting to software rendering

Those were the only two EE entries in the log.  Unfortunately, I'm not sure what either meant, but I'm going to do some searching on them...ring a bell for anyone?

---

### Post by redwarrior on 2007-11-10
I'm getting closer!  I solved the error "2:  Digital Input Cannot Display This Video Mode."  It turns out, thanks to a Fedora forum, this error just means that the default settings in xorg.conf for the horizontal and vertical refresh/sync rate need to be changed to fit the compatible ranges for your monitor, which are easy to find on Dell's website if you go to the specifications page in the manual for your monitor.

Now all that remains is getting hardware acceleration to work.  I don't know about anyone else, but mine won't even boot to the GUI without it and I see from the multimedia and video forums that it's a known issue.  I'm going to continue this post over there now that I'm on to a ATI Radeon specific issue rather than a Dell specific issue, but I wanted to share what I found on that initial error in case anyone else here runs across it!

---

