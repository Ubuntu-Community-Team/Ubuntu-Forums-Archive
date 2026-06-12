---
title: "Remote desktop broken"
date: 2007-05-24
forum: Desktop Environments
---

### Post by stewymcstewstew on 2007-05-24
I don't know if this is a common problem, I searched around for awhile but could find no solution.  All of a sudden when I try connecting to my Buntu 6.10 box via VNC it will not accept any password no matter how many times I change the password (using the command "sudo gconftool-2 -s -t string /desktop/gnome/remote_access/vnc_password Password").  

It will not accept any password I enter, it has not been doing this for very long it recently happened (I believe after an upgrade).  I only really have SSH access to it as I don't want to haul a monitor out to plug into the box.  

Thank you in advance.

---

### Post by Kobalt on 2007-05-24
Did you enable the Remote Desktop in System > Pref. ?

---

### Post by stewymcstewstew on 2007-05-24
Yeah it worked perfectly for awhile but after a system wide upgrade it decided to stop accepting the password I had been using.  Reseting the password wont work.

---

