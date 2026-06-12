---
title: "Login Loop Lightdm"
date: 2013-12-13
forum: Desktop Environments
---

### Post by kyosaku on 2013-12-13
Dear Veterans,

I desperately need help on following issue:

After installing latest proposed nvidia Xorg driver (304.116) manually on Ubuntu 12.04.3, system startup did not work as usual and I had to restore / partition using LIVE-USB Clonezilla in order to restore normal working order. So the system went fine again after that: I could login as normal in my user-session and start loading all other updates, except the nvidia of course, and then I rebooted.

After another reboot, there is just no way to get back into my user-session using lightdm: the screen just loops back into to login !

What works:
1. using tty to login, stopping lightdm, starting gdm instead - I can normally login with my user then - also I can see all contents of my encrypted home folder.
2. logging in using guest account works with lightdm
3. creating new user account with lightdm and loggin in

Solution tried:
  deleting .Xauthority and .ICEauthority in home folder

I guess one solution would be to migrate my user-account to another and copy all the files from one home-folder to another. But I wanted to ask first if anybody knows a smarter way to solve this problem ?

Thank you all for your suggestions !

---

