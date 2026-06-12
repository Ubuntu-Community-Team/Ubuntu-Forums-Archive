---
title: "Huge problems with desktop effects (restricted driver and open source now)"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by bootsbradford on 2007-10-20
I am so frustrated! :mad:

Compiz-fusion was running fine following my upgrade to Gutsy. I have an ATI Radeon X600 card and I was running the open source 'ati' driver. I had the occasional freeze - nothing as bad as under Feisty, but I thought I would try to restricted driver.

I installed xserver-xgl and the restricted driver. I then rebooted **but was faced simply with a black screen and nothing else.**

Using the recovery mode, I reconfigured xorg using:

```
dpkg-reconfigure xserver-xorg
```

I assumed that, at the very least, everything would now be back to how it was before, since my xorg settings were the same as before I installed the restricted driver. Oh no...

Now when I go to reenable Compiz-Fusion I am told **"Desktop Effects could not be enabled"**. 

If I type in compiz --replace into terminal, I am given this output:

> mark@mark-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:3e50 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


Nothing ever seems to go smoothly with Ubuntu. Can anyone help me sort this out?

---

### Post by Faud on 2007-10-20
did you redownload the open source driver ?

---

### Post by Faud on 2007-10-20
also you can check out this thread

[http://ubuntuforums.org/showthread.php?t=582207](http://ubuntuforums.org/showthread.php?t=582207)

---

### Post by bootsbradford on 2007-10-20
> **Faud said:**
> did you redownload the open source driver ?

How should I do this?

---

### Post by bootsbradford on 2007-10-20
The problem was not removing fglrx properly, though I thought I'd already done this.

```
sudo apt-get remove xorg-driver-fglrx
```

It's worked fine from this point onwards!

---

