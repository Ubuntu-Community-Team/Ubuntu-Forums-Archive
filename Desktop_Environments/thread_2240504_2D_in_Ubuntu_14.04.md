---
title: "2D in Ubuntu 14.04"
date: 2014-08-20
forum: Desktop Environments
---

### Post by Azyx on 2014-08-20
Have made a new install of Ubuntu 14:04LTS on a machine who had 12.04 before. I have the computer/server mostly as a desktop, that I by habit also controll, from another room with VNC (Desktop sharing). It's an E450M1-M and ATI propretarian drivers installed with Additional-drivers. When I have 12.04 I used 2D-desktop because, It get very slow and used a lot of power with 3D-desktop. I wonder how I may log in as 2D or fix, so 3D work fine from an 12.04 and 14.04 client.

Additional info.
BTW. I can connect to a 3D-unity, AND the mouse can move windows and I can even type "åäö", but from the client, there are no update of the desktop. Disconnect och connect again are no solution, but it works. So the problem is signal from vnc-server to the client.

There is the same problem with both 'Remote Desktop Viewer' and 'Remmina remote desktop client'. Updated event does not update.

---

### Post by Frogs Hair on 2014-08-20
The 2D session was removed in 12.10 and what you might want to do is install gnome-session-flashback and use the low resource metacity/ no effects session.

---

### Post by coldraven on 2014-08-20
I think that 2D is not supported in 14.04, maybe you should have stayed with 12.04.
You could try Xubuntu or Lubuntu 14.04 that should be faster.

---

### Post by Azyx on 2014-08-20
I worked fairly good on ASRock ION 2x1,6GHz Nvidia propretatian drivers with Ubuntu 14.04, so.... well..will see how I do? I made a new istall, because i hade installed ATI, propretaiian Catalyst things and 12.04, complained about incompability with hardware frameworks or something. Antother way maybe to uninstall ati-propretarian drivers (it worked but poor, with the open drivers)... I have just start to love Unity, so Xubuntu/Lubuntu is not so apropiate for me :( What is the diffenens between gnome-session-fallback and gnome-session-flashback?

---

### Post by Frogs Hair on 2014-08-20
The fallback package was renamed and is now a dummy package.

---

### Post by grahammechanical on 2014-08-20
Gnome session fallback was what people installed who were using Ubuntu 12.04 if they wanted what they called the "Classic" look. On 14.04 to get that look we install gnome-session-flashback because that is the name of the package. We get two additional login options. Gnome Flashback (Compiz). Gnome flashback (Metacity).

In 14.04 "Classic" is a Gnome 3 shell extension. Install Gnome classic and we get Gnome 3 shell as well.

In 12.04 Unity 2D was used as a fall back user interface for those graphic cards that could not run Unity 3D. In 14.04 this problem is dealt with by using an open source video driver called llvmpipe. It runs Unity 3D on cards that cannot do hardware acceleration but it runs it slowly. So, there was no need for the Unity 2D code. It was removed.

Regards.

---

### Post by Azyx on 2014-08-20
By some reason Vino worked with Unity 2D, but not well at all with Unity 3D, by some reason on 12.04. Even if there where some problems, like  with Swedish letters, åäö, but with some log--in/log out, it worked. No the problem is that the Vino-server don't send back events on the desktop, but I can controll the Vino-server...

---

### Post by Azyx on 2014-08-21
I have no uninstalled fglrx-drivers  with Add-drivers and installed the open drivers. 50% CPU-power use with connecting remote-desktop viewer, are better than no connection at all. Will try to solve the extrem CPU-use. Thanx for all tips, and if someone know how I can get better performance, or 2D accerelation for VNC-server (Vino-server)?

Cheers

---

