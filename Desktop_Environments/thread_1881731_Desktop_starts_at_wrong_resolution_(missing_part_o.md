---
title: "Desktop starts at wrong resolution (missing part of desktop)"
date: 2011-11-16
forum: Desktop Environments
---

### Post by OneOfMany07 on 2011-11-16
I had an Nvidia 8800 GTX installed on Ubuntu 10.10, and everything was fine using the nvidia v280 drivers I installed manually to use with CUDA 4.0's SDK.  Had worked originally with Novouex before too, or however you spell it.

Then I got a free Nvidia 260 216 card and figured why not use it.  This card worked fine in Windows 7 x64, but rebooting into Ubuntu gave me a desktop that looks shifted to the left and up.  With part of the left and top of the desktop being off screen.  Also I think I saw in my monitor's settings that it is running at 720p versus the 1920x1200 native resolution.  This monitor was sold as a computer display, but needs me to use a DVI (computer) to HDMI (monitor) cable if that matters.

Next I replaced that 260 with an Nvidia GTX 480.  Again card works fine in Windows, but in Ubuntu the shifted and lower resolution display.

I didn't worry about it for a bit, but now I'd like to try to fix it.  I just tried erasing my old partition and installing Ubuntu 11.10.  Hit a grub2 issue (some wrong elf architecture message) that I've fixed with a Google search, but having the same display issue now.  I have not installed the nvidia drivers yet.  Mostly as it didn't work before, and that I can't see the screen to bring up the display properties.

Note I did not have this issue when booting from my USB stick (had to use UEFI mode, for some reason booting as USB didn't work).  This is both during install and when I selected to run it as trial to fix grub2.  That tells me the hardware can work, but it likely is a configuration issue.  That the configuration between the run from DVD and the installed default are different.

I found a thread that talked about using "read-edid", but all it output was "parse-edid: parse-edid version 2.0.0" and no shell prompt again.

I'm guessing I might be able to resolve it with some manual xorg.conf edits, but this seems like it shouldn't be necessary on fairly current hardware and a vanilla config.

Thanks for any help in advance.

---

### Post by Copper Bezel on 2011-11-17
Normally I'd suggest Google searching for your specific card and Ubuntu version, but I'm finding very little, and from what I did find, there *are* people successfully using this card under 10.10, [_as well as 11.10_]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/881467"). It's passing strange that it would work from the LiveCD but not from the install; still, I'd try the proprietary drivers first, since they'll be different from the ones you tried under 10.10. It's possible that the HDMI interface could be the culprit, too, but I'm not very well versed in this hardware stuff.

You might just need to file a bug and see if anyone else is experiencing the same problem, and you might want to try it with another monitor (if that's an available option) to see if the interface is the issue.

---

### Post by OneOfMany07 on 2011-11-17
Thanks for the suggestions and the extra time searching Google.  I didn't find much, but I was looking for my problem versus looking for working examples.

I originally saw it happen using the Nvidia proprietary drivers after the first card swap.  So I'm guessing it won't do much, but can't hurt.

Thankfully a friend suggested using VNC from another computer to let me see the whole screen.  Otherwise I'm not sure I could even try installing the other driver, or tweaking other system settings.

I'll probably need to file the bug to get more technical help.  Thanks for that suggestion too.
---------------------------------
Now shortly after it automatically logs in I get a black screen, then a set of white dots are evenly spaced about 3/4 of an inch between them across whole screen.  And after that happens ctrl-alt T doesn't work anymore.

I'm wondering if this is related to me having two video cards installed, but not in SLI and not both same chipset.  CUDA programming and debugging can benefit from that (not that I'm doing it right now).  I swear I tried removing the second card before, but who knows.

---

