---
title: "Steam Not Launching"
date: 2013-02-15
forum: Gaming &amp; Leisure
---

### Post by MNKYband on 2013-02-15
Hello,

I just installed Ubuntu on my desktop computer, mostly because of the Steam event, but when I finally figured out how to install Steam, it would not launch properly. I have no idea what to do, and would like some help.

When I click the button in the taskbar, it flashes for a minute and then goes back to normal, and nothing else happens. I am extremely new to Ubuntu and have no idea what I am doing, so I apologize for the lack of information. If anyone could help me, I would greatly appreciate it.

---

### Post by Perfect Storm on 2013-02-15
Hi MNKYband, welcome to the Ubuntuforums :)

If you could fill in some info on your computer it would be nice and which version of ubuntu you use adn if it's 32-bit or 64-bit.

Lets see what is happening behind the scene:
1. click the super button (the one with the windows logo).
2. type 'terminal'
3. Click on the terminal icon.

in the terminal write(copy/paste):
```
steam
```

Post the output of that command.

---

### Post by MNKYband on 2013-02-15
I have an IBM dual core computer with an Intel graphics card, running Ubuntu 12.04 32-bit.

Here is the result of the steam command:

```
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1360841030_client)
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadAlloc (insufficient resources for operation)
```

Thanks for helping me with this!

---

### Post by Perfect Storm on 2013-02-15
Valve and Ubuntu are recommending that you update the driver for your video card: [https://wiki.ubuntu.com/Valve#Intel_Graphics](https://wiki.ubuntu.com/Valve#Intel_Graphics)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade
```

Reboot.

Then try again.

---

### Post by MNKYband on 2013-02-15
I should have thought of that, actually :I

It doesn't seem to have done anything, though. I'll leave the computer for a bit, and I'll let you know if it launches.

---

### Post by Kiori on 2013-02-15
Can you specify which Intel card you've got?
Cause not all of the Intel cards are playing games atm.
Not that this should affect launching the client.
I have ran the Steam for linux client even on a intel i965, and a HD3000, so it should work fine.

---

