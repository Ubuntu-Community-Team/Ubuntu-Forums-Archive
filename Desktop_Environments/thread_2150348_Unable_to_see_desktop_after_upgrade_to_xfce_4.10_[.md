---
title: "Unable to see desktop after upgrade to xfce 4.10 [SOLVED]"
date: 2013-05-31
forum: Desktop Environments
---

### Post by rmcellig on 2013-05-31
I am using Linux Lite (xfce 4.8, thunar 1.2.3, ubuntu 12.04). I went to upgrade to xfce 4.10, thunar 1.6). When I restarted the machine, I got as far as entering my login info. After that, just a black screen, no desktop. What should I do to get back to normal?

---

### Post by sudodus on 2013-05-31
If you can run text screens with*** ctrl + alt + F1*** you can remove xfce 4.10 and reinstall 4.08 from there and try again after reboot. Otherwise you might be able to run a text session by adding the boot option **[FONT=courier new]text[/FONT]** at the grub menu entry at **[FONT=courier new]quiet splash[/FONT]**

---

### Post by rmcellig on 2013-05-31
Thanks  sudodus!

That's what I had in mind I can get to ctrl+alt+F1 no problem. What exactly do I have to type at the command line to remove xfce 4.10 and reinstall 4.8?

---

### Post by rmcellig on 2013-05-31
Thanks  sudodus!

That's what I had in mind I can get to ctrl+alt+F1 no problem. What exactly do I have to type at the command line to remove xfce 4.10 and reinstall 4.8?

---

### Post by sudodus on 2013-05-31
How did you install it? If you used apt-get, run sudo apt-get remove package-name. If you installed from a manually downloaded file, try to uninstall using that file and some command line option.

---

### Post by rmcellig on 2013-05-31
I installed from a ppa.

Once I remove sfce 4.10, how do I install 4.8?

---

### Post by rmcellig on 2013-05-31
This is what I used to upgrade to 4.10:

sudo add-apt-repository ppa:xubuntu-dev/xfce-4.12
sudo apt-get update
sudo apt-get upgrade

---

### Post by sudodus on 2013-05-31
Is xfce-4.08 that you used earlier available in any of your repos or via a ppa? Or do you still have the package in the apt-cache? In that case, try to install it. Maybe you need to remove the ppa.

---

### Post by rmcellig on 2013-05-31
Everything is working fine now. All I did was sudo ppa-purge the ppa name

This brought me back to where I was before. Looking good!! :)

---

### Post by sudodus on 2013-05-31
Congratulations  :KS

---

### Post by rmcellig on 2013-05-31
Thanks! Now how do I mark this solved?

---

### Post by sudodus on 2013-05-31
Edit your first post, go advanced and change the prefix to SOLVED (until the old standard method comes back)

---

