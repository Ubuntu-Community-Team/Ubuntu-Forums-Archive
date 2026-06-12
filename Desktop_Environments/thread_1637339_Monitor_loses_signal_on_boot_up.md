---
title: "Monitor loses signal on boot up"
date: 2010-12-04
forum: Desktop Environments
---

### Post by MusicallyInspired on 2010-12-04
I have a Pentium 4 2.8Ghz 768MB RAM with a nVidia GeForce FX 5200 AGP card. This just happened out of the blue. Beforehand everything was fine. But now every time I do a new install this still crops up. The problem seems to have just created itself out of nothing. Once it gets past the BIOS boot process the splash screen appears for a second and disappears mid-loading and never comes back. Shortly after that the monitor loses the video signal. I've tried fresh installs of Ubuntu and Ubuntu Studio with the same results. Initially Kubuntu wouldn't even load up from the live cd, but then it worked afterward. I might try installing that one and see where it gets me.

I've tried running in recovery mode and booting with failsafe graphics mode, but when I choose "Run Ubuntu in low-graphics mode for just one session" it shows a window that says "Stand by one minute while the display restarts..." and never does anything unless I click OK, and when that happens it brings me back to the recovery menu and doesn't boot up the X Server at all.

If I choose Reconfigure Graphics it takes me a to a window where I have 3 options: "Use default (generic) configuration, Create new configuration for this hardware, and Use your backed-up configuration". No matter what I choose, however, it just brings the very same window up and I get nowhere.

I've booted into the root shell in recovery mode and removed and installed nvidia-current a hundred times and tried booting with both of them but neither of them work. Again, nomodeset is already in grub as default for all boot options. Any other ideas? If all else fails I may just try booting with the on-board graphics card.

**EDIT:** It seems to work with my onboard graphics card, but I'd really rather work with my nVidia card if possible. Especially considering it was working fine beforehand. It's weird. I was using it a few months ago with no problems. After all this time I decided to boot up my linux machine again and then this no signal thing comes up.

---

### Post by smo0th on 2010-12-04
it could be the card is being configured with a resolution not supported by your monitor, did you already specified any resolution?

---

### Post by MusicallyInspired on 2010-12-04
Yeah, my maximum LCD monitor resolution is 1024x768 and that's what it was set to in GRUB. Either way, I'm running on my onboard card now and it's running at 1024x768. If I switch to the nVidia card it goes blank. Could they have different settings depending on which card I'm using? How can I confirm that?

---

### Post by oldfred on 2010-12-04
I have a newer Nvidia and the monitor always goes to sleep on install or first boot. But once I install the nvidia driver it works. Not sure if the older Nvidia card uses the same driver or not.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

If able to boot to recovery mode & netroot or your install.
list of recommended drivers, mine now only shows nvidia
jockey-text -l
Install a driver
sudo jockey-text -e <driver>

---

### Post by MusicallyInspired on 2010-12-04
As I said earlier, it's already set to nomodeset. It always has been. I can't boot up the X server even when it's set to nomodeset.

---

### Post by wannacme16 on 2010-12-04
I don't know how much help this might be but I had a similar problem that was caused by an extension that I had purchased to allow my monitor to reach my tower, factory monitor plug to short. The extension worked for a while but went dead and I experienced some of what you are. I took out the extension and used the short monitor cord and it worked. Maybe it be something simple as a cable. It was for me.

---

