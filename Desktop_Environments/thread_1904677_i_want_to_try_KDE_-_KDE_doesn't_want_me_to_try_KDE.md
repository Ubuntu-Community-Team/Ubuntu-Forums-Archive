---
title: "i want to try KDE - KDE doesn't want me to try KDE"
date: 2012-01-05
forum: Desktop Environments
---

### Post by lakitu on 2012-01-05
hey - 

trying to install the kde desktop enviornment as given simply & easily on Psychocat's tutorial.

this is the error Details gives me in Synaptic Package Manager.

> E: /var/cache/apt/archives/kubuntu-firefox-installer_10.10ubuntu4_amd64.deb: trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package firefox 9.0.1+build1-0ubuntu0.10.10.1

i tried deleting it as root, but no such luck. (i still get the same error.) 

any help in the alps? it says Kubuntu when i start up, but unless KDE is exactly like Gnome, it's not KDE.

---

### Post by carl4926 on 2012-01-05
You have to switch session at the login screen

---

### Post by lakitu on 2012-01-05
ok =)

duh.

(that worked) - the thing that deked me out was, "Kubuntu 10.10" or whatever was what showed up when loading, so you'd assume Kubuntu 10.10 (or whateveR) would be loading. 'fraid not mcfly. lol

ok - at first the install would fail (at that point) - using Software Center, but then it eventually completed i think.

anyway - i'm kde-in' now, thanks. might be time to upgrade my graphics card so it actually runs...

---

### Post by N00b-un-2 on 2012-01-05
try purging firefox.  Then you can reinstall it later.  The reason it says "Kubuntu 10.10" at loading is because what you're looking at is a plymouth theme.  When you install the kubuntu-desktop package it overwrites the default purple ubuntu plymouth theme.

To use KDE, you have to select "Kubuntu Session" at the login screen.

EDIT:

Oops, I didn't see that you had already solved it.  I was on KDE for a while and it was pretty sluggish on both the Intel graphics as well as the ATI Radeon card.  I recently upgraded to an nVidia GeForce 8800GTS but I haven't give KDE a shot since.  Maybe I should...

---

