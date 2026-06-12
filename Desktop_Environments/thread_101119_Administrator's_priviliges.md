---
title: "Administrator's priviliges"
date: 2005-12-09
forum: Desktop Environments
---

### Post by migueljacq on 2005-12-09
Hi all,

Just giving Kubuntu a try, dual booting on existing Ubuntubook :-)

I was trying to configure the network settings (ethernet) and the GUI tells me I need to click on the Administrators Priviliges button to edit. I do so, I get prompted for a password, I enter it, the screen goes back to the menu but I still can't edit. And it still tells me I need the priviliges.

I know I'm a sudoer because, ubuntu sets it up at installation, and also, I've been editing some files (i.e fstab) with sudo priviliges.

Anyone know what the problem is?

Cheers

---

### Post by Zaventh on 2005-12-09
Did you just perform an upgrade (ie. Hoary>Breezy or KDE 3.4>3.5)? Sounds like DCOP isn't working properly... I've had this happen to me before on Fedora. You might try reinstalling KDE.

---

### Post by aysiu on 2005-12-09
Try Alt-F2 then typing in this command ```
kdesu kcontrol
``` Any difference?

---

### Post by Sokraates on 2005-12-09
Adminmode is faulty in kcontrol. It's a nknown bug.

Start kcontrol as root (like aysiu told you) and you should be okay.

As an alternative to kcontrol you can try systemsettings, though it supports less options than kcontrol.

```
sudo apt-get install kde-systemsettings
```

---

### Post by migueljacq on 2005-12-09
Cheers, aysiu's 'kdesu kcontrol' did the job. Thanks again!

---

