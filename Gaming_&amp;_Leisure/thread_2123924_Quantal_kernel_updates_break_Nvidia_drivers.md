---
title: "Quantal kernel updates break Nvidia drivers"
date: 2013-03-09
forum: Gaming &amp; Leisure
---

### Post by jasoncallaway on 2013-03-09
Just a heads up to the community...

My 12.10 box's Nvidia drivers take a dive each time the kernel gets updated.  It seems to be due to the fact that nvidia-current requires the kernel version specific linux-headers package.  For some reason the dependencies aren't built to intsall a new linux-headers with a new kernel.

Workaround follows.  Hat tip to [http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html) which helped me get installed the first time.

After you update the kernel, but before you reboot, do the following.

    [FONT=courier new]$ sudo apt-get install -y linux-headers-`uname -r`
$ sudo apt-get remove nvidia-current
$ sudo apt-get install -y nvidia-current[/FONT]

If you don't do this, things can be tricky after the reboot, especially if you're using a dual-monitor setup.  My Alienware m18x has an HDMI out, which I use as my primary display.  When the Nvidia module is unable to load, the dm forgets about my monitor settings.  I can log in, but I get no menu or sidebar.  There's a work around here too, though.

On the working monitor, right-click on the desktop and make a new folder.  Open folder, and use Nautilis to search for 'terminal'.  Be sure to set Location to 'File System'.  Look for the 'Terminal' icon, and not 'Terminal.svg', which is the scalable vector graphic icon.  You could reboot into run level 3, but this is easy.

Later I'll work on troubleshooting the dependency problems.  I'm a recent convert from Fedora, but as I understand it, pre-Quantal versions did not experience this error, which leads me to believe that previous deb dependencies could be used to fix this.

Hope this helps.

~Jason

---

