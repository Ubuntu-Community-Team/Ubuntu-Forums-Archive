---
title: "first boot after install of Wubi 8.1"
date: 2008-12-31
forum: General Help
---

### Post by rs1372 on 2008-12-31
I have a desktop ( HP pavilion 752n) with a fresh installation of windows xp fully updated, and I used wubi 8.1 to install ubuntu.  I had plenty of space on the hard drive (20 GB) and I chose to use 10 GB in the installation and used the Ubuntu distro option.  The entire installation process went fine (no error messages), and Ubunto boots when I choose so at startup.  I type in my username, and then my password.  After that the screen stays a tan color but it nothing shows up except for the mouse cursor.  The cursor will move when i move the mouse, but nothing else is on the screen...

What do I do to get Ubuntu to load properly?

---

### Post by abn91c on 2009-01-01
press ctrl+alt+f1, at the prompt type these commands one at a time, the problem it the desktop effect that ubuntu loads by default
sudo apt-get remove compiz
sudo apt-get remove compiz core
after they are done sudo reboot

---

### Post by rs1372 on 2009-01-02
I did what you said, and after the sudo reboot, it contiued to do the same thing as before.

I then tried to login using GNOME failsafe mode, and this did not change anything for me either.
If I log in with Terminal failsafe mode it gives me a prompt similar to the one I reached by pressing ctrl+alt+f1.
I am sure that compiz was successfully uninstalled. The second time I tried to unistall compiz, it said:

...package compiz is not installed, so not removed 
0 upgraded, 0 newly installed, 0 to remove and 203 not upgraded

Thanks for your help so far, what should I do now?

---

### Post by iXXer on 2009-03-22
I had a similar problem, I installed Ubuntu from the Live CD but had to run the installer instead of the Live CD portion. To fix mine I booted to [failsafe] from the Grub menu(pres ESC) and dropped to a root console prompt. I then did
```

apt-get remove compiz
apt-get remove compiz-core
exit

```
I then ran xfix from the menu after it finished I continued the normal boot. It came up fine for me after this and I was able to log in and view my desktop.

Good luck, hopefully that fixes you too.

---

