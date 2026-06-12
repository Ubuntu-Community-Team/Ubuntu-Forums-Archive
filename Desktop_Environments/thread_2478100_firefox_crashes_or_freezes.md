---
title: "firefox crashes or freezes"
date: 2022-08-16
forum: Desktop Environments
---

### Post by mike010 on 2022-08-16
Firefox crashes or freezes i read somewhere its a problem with that snap package of Firefox does anyone know of a fix for this?

---

### Post by deadflowr on 2022-08-16
> Firefox crashes or freezes i read somewhere its a problem with that snap package of Firefox does anyone know of a fix for this?
I've never had it freeze or crash, but if you want you can test the theory that it is snap related by removing the snap version and installing the deb version.
See:[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04]("https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04")

---

### Post by ActionParsnip on 2022-08-17
If you make a new Firefox profile. Does it work OK there?

---

### Post by mIk3_08 on 2022-08-18
> **mike010 said:**
> Firefox crashes or freezes i read somewhere its a problem with that snap package of Firefox does anyone know of a fix for this?
I agree with deadflowr remove the snap firefox and install the new firefox via deb or to the other package manage. Like Flatpak. I always use my Firefox and I never encounter any error ever since. Firefox run smoothly on my Linux Ubuntu Operating System. Regards and cheers
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290880&stc=1[/IMG]

---

### Post by grahammechanical on 2022-08-19
I do not think that this is happening because Firefox in Ubuntu 22.04 is a snap packaged application. It is because of something called systemd-oomd. 

[https://www.omgubuntu.co.uk/2022/06/ubuntu-22-04-systemd-oom-killing-apps](https://www.omgubuntu.co.uk/2022/06/ubuntu-22-04-systemd-oom-killing-apps)

Is your system fully up to date? I experienced this several weeks ago but no longer.

Regards

---

