---
title: "Difference between &quot;(XYZ)buntu&quot; &lt;-&gt; &quot;ubuntu server + window management&quot;?"
date: 2010-10-29
forum: Desktop Environments
---

### Post by Seeb on 2010-10-29
Hey there,

can anybody tell me if there is a difference between the following installations:
Ubuntu <-> Ubuntu server + gnome
Kubuntu <-> Ubuntu server + KDE
..and so on

I don't mean the difference for each and any distri but the difference in general: (XYZ)buntu and ubuntu server + window management.

The reason I'm asking is because I really like Ubuntu and I really like Openbox. But since im running into many troubles using Lubuntu (PLUS theres way too many apps preinstalled for my taste) I'd like to try a Ubuntu server installation + Openbox. 

Greetings
Seeb

---

### Post by 3Miro on 2010-10-29
I don't know if there are any differences in terms of applications installed (I would imagine there would be), however, I know that the kernel for the server edition has changes in the way it manages the CPU. Server builds of the kernel make the system work more chunky under load, however, they produce more result over a long period of time (which is what you would expect from a server).

If you don't like the amount of software that is pre-installed, you can try to use and alternative install. From the boot screen where you choose "Try" vs "Install" you can hit F4 and tell it to install a CLI system only (not graphics). Then you can go in and install only the apps that you want (however, you will have to know what you are doing).

I don't know what kind of trouble  you are running into with Lubuntu, but every time I try LXDE is tends to be somewhat unstable, the whole thing is too new I suppose. On the other hand, I really enjoyed working on Gnome + Open Box. All you have to do is install Ubuntu (with Gnome), then install Open Box and Fusion Icon, form the icon you will be able to change the window manager.

---

### Post by Seeb on 2010-10-29
Hey 3miro,

thanks for your reply.

LXDE wasnt unstable for me but I'm facing 3 kinds of troubles
1) After a few minutes of watching a video stream fullscreen (youtube, etc.) my display goes totally crazy which means that it starts to flare and flicker and you cant see anything anymore.
I know this is a graphic driver related issue (already tried using fglrx) but I had the same driver with xubuntu where it used to work
2) transparency isnt working with xcommgr (I tried any tutorial, and I did it RIGHT! ;) )
3) tilda doesnt seem to like working under LXDE, giving back several errors while being used exactly like in my xubuntu installation, where it hadnt have such problems

Thats why I'd like to start an installation from scratch, just having installed what I need and knowing what I installed ;)

I think I'll try the alternate installation then, if the server handles the CPU otherwise.
If it wont work with ubuntu alternate install + openbox I think I'll just try an (X)Ubuntu installation with openbox!

---

### Post by 3Miro on 2010-10-29
I have never done XFCE with OpenBox, I find Xfwm4 more than adequate (it even has nice in-build composition for transperancy). Try that first.

For the video installation, check with the GPU temperature. It sounds like it is overheating.

---

