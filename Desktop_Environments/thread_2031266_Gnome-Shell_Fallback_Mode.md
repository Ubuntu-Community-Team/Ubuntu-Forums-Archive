---
title: "Gnome-Shell Fallback Mode"
date: 2012-07-21
forum: Desktop Environments
---

### Post by Thunder7102 on 2012-07-21
Hey guys. I am running Ubuntu 12.04 64bit with Nvidia proprietary drivers running off of a Nvidia GTS 450. For some reason when I start gnome-shell, it keeps putting me in fallback mode. Any idea why?

---

### Post by Frogs Hair on 2012-07-22
When searching the forums 8 posts were located regarding that graphics card and the Gnome Shell and none were solved or were different problems. You may have to wait for someone using that card . I run an earlier Nvidia card and don't have any problem using the current proprietary driver.

---

### Post by bogan on 2012-07-22
Hi!, **Thunder7102**,

I do not have a GTS 450, but  GT520, which runs very well with the default nouveau driver; but I have also run it, and a GT7650,  with the nvidia proprietry drivers.

By: " when I start gnome-shell, it keeps putting me in fallback mode." do you mean 'Gnome Classic, 'Gnome Classic (no effects), or unity-2D?

If you are in doubt run:```
 echo $DESKTOP_SESSION
```Have you tried the ( nvidia-current (post release updates)version from Additional drivers? or the later one from x-swat/x-updates ppa?

There are much more up-to-date [released & beta] versions available from nvidia.com/Downloads.

Chao!, **bogan**.

---

### Post by Thunder7102 on 2012-07-22
> **bogan said:**
> Hi!, **Thunder7102**,

I do not have a GTS 450, but  GT520, which runs very well with the default nouveau driver; but I have also run it, and a GT7650,  with the nvidia proprietry drivers.

By: " when I start gnome-shell, it keeps putting me in fallback mode." do you mean 'Gnome Classic, 'Gnome Classic (no effects), or unity-2D?

If you are in doubt run:```
 echo $DESKTOP_SESSION
```Have you tried the ( nvidia-current (post release updates)version from Additional drivers? or the later one from x-swat/x-updates ppa?

There are much more up-to-date [released & beta] versions available from nvidia.com/Downloads.

Chao!, **bogan**.
When I used the echo cod e you gave me, I got gnome-shell.
And no, I am not using unity 2D. I downloaded and installed gnome to not use unity. My interface looks a lot like Gnome 2 and when I tried running the post release update version from additional drivers, my computer would not properly boot. Even the safe-boot option had an endless boot time of processes timing out. I had to have someone walk me through using a bootCD and entering commands to my system .

---

### Post by bogan on 2012-07-23
Hi!, **Thunder7102,**

In 'fall-back' you would have 'Applications' & 'Places' menu headings, giving Gnome2 style drop-down Menu listings, with top & bottom Panels.

Whereas, in gnome shell the 'Activities' menu heading gives access to a Unity style Launcher & a 'Dash' style Application display.

It looks to me as if you have a faulty Gnome installation, but I do not know exactly what commands are needed to remove, purge and re-install it.

Hopefully, someone more knowledgeable in that field will come in.

Best of luck,

Chao!, **bogan**.

---

### Post by Thunder7102 on 2012-07-23
> **bogan said:**
> Hi!, **Thunder7102,**

In 'fall-back' you would have 'Applications' & 'Places' menu headings, giving Gnome2 style drop-down Menu listings, with top & bottom Panels.

Whereas, in gnome shell the 'Activities' menu heading gives access to a Unity style Launcher & a 'Dash' style Application display.

It looks to me as if you have a faulty Gnome installation, but I do not know exactly what commands are needed to remove, purge and re-install it.

Hopefully, someone more knowledgeable in that field will come in.

Best of luck,

Chao!, **bogan**.
As you have said, I have the applications and Places menu headings.

---

### Post by bogan on 2012-07-24
Hi!, **Thunder7102,**

So, although you are logged in as 'Gnome', ie. gnome-shell, your display is in 'Gnome Classic ( no effects)', ie. fall-back session.

I am no expert in this matter, but If I were in the situation you describe I would do the following:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg-reconfigure -a # may take a long time with no feed-back
# if that does not work, then:
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install --reinstall gnome-terminal
sudo apt-get install --reinstall gnome-shell
```Checking if each command, after dpkg, alters things. 

Please Post: ```
 /usr/lib/nux/unity_support_test -p
```Chao!, **bogan.**

---

