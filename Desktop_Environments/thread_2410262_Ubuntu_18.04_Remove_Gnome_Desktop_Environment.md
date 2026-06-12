---
title: "Ubuntu 18.04 Remove Gnome Desktop Environment"
date: 2019-01-13
forum: Desktop Environments
---

### Post by Redalien0304 on 2019-01-13
Have Installed Ubuntu 18.04 Bionic. I Always Install Cinnamon DE & Switch over to it. 
Is it Possible to Remove the Default Gnome DE?? in Ubuntu 18.04??
Only thing i have seen so far on is here [https://www.reddit.com/r/linux4noobs/comments/9a18x5/how_to_remove_default_ubuntu_desktop_1804/](https://www.reddit.com/r/linux4noobs/comments/9a18x5/how_to_remove_default_ubuntu_desktop_1804/)
 & here [https://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16](https://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16) which is for 16.04.

Only thing i have tried is [FONT=Noto Mono, Menlo, Consolas, Courier New, monospace]sudo apt purge ubuntu-desktop sudo apt autoremove. which did not remove it from the Desktop Selection when you Login[/FONT] 
[FONT=Noto Mono, Menlo, Consolas, Courier New, monospace]I Have tried Linux Mint 18 & 19 i just prefer Ubuntu 18.04 with Cinnamon DE.[/FONT]

---

### Post by drlamb on 2019-01-16
If your goal is a simple Ubuntu install with the Cinnamon DE what I'd do is use the Server ISO to install a Minimal Ubuntu installation before then installing only cinnamon. That way you wouldn't have GNOME shell or any of its recommended packages installed. Note that the only other significant difference you'll see if you go this route is Netplan being used instead of NetworkManager, but that can be easily fixed. If you want more information about how to do this please let me know.

---

### Post by Redalien0304 on 2019-01-16
ok sure Thanks for the Info. Netplan?? Can you replace it with NetworkManager?? And whatever else can removed or replaced? So it is no longer a Server Installation?

---

### Post by drlamb on 2019-01-16
Correct, there's really no difference. It's still Ubuntu. You'd need to modify the netplan configuration to allow NetworkManager to take over. 

/etc/netplan/01-network-manager-all.yaml:

> # Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

---

### Post by ajgreeny on 2019-01-17
Rather than a server image I suggest you use the minimal install CD version; there will be nothing to remove from that such as netplan, and it may be even simpler for you.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Redalien0304 on 2019-01-18
Found a Solution using the Ubuntu Minimal Install CD & installed Minimal DE & then Installed Cinnamon DE & Remove initial Minimal DE that was Selected during install.

---

### Post by Redalien0304 on 2019-01-18
Created a Customized Live USB with only Cinnamon DE Installed.

---

### Post by drlamb on 2019-01-28
> **ajgreeny said:**
> Rather than a server image I suggest you use the minimal install CD version; there will be nothing to remove from that such as netplan, and it may be even simpler for you.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's a shame that the minimal isos still don't support UEFI.

---

### Post by callistagraves on 2019-01-31
Okay, just got into this thread, and noticed your comment.

My question, then, is installing 18.04 via the MinimalCD option problematic when it comes to wifi drivers?   I know I was looking at the Debian NonFree live image/install iso, and it's got the iwlwifi ready to rock, so I wonder if Ubuntu does as well?

I sure would love a more minimalist setup.

---

### Post by wildmanne39 on 2019-01-31
Hello callistagraves, please start your own thread so you and the OP of this thread can both get the help your deserve.

Thanks

---

### Post by yetimon_64 on 2019-02-05
From ajgreeny post #5 ...
> Rather than a server image I suggest you use the minimal install CD  version; there will be nothing to remove from that such as netplan, and  it may be even simpler for you.

+1. The minimal installer makes for a very clean install but may be difficult to use for some users, particularly if UEFI mode is needed.

> **drlamb said:**
> It's a shame that the minimal isos still don't support UEFI.

It is still possible to get a minimal installer to install in UEFI mode with files supplied in the minimal iso, it just needs a bit of coaxing to do so.

I used a guide [[COLOR=#0000ff]--here--[/COLOR]]("https://www.onetransistor.eu/2015/12/install-ubuntu-minimal-cd-uefi-enabled.html") to do so with 14.04 a few years ago and have just built up another 18.04 miniefi installer USB stick using this same information that just booted up to an installer boot screen.

In trying this with 18.04 I found it pays to show hidden files before copying the installer files to the temporary hold folder; there is a hidden folder ".disk" on the Bionic installer that when initially left out caused the USB stick to fail to boot; it was either that reason or possibly not having a volume label on the FAT32 partition that could have caused the failure on my first attempt. After adding a volume label, I called mine "MINIEFI" like the author in the link used on his desktop temporary folder, and showing hidden files/folders the second attempt with the USB stick installer worked fine. I will be using it to install an 18.04 minimal system on a UEFI hardware set up here as I did with my Trusty install a few years ago.

---

