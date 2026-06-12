---
title: "Missing Unity Menus"
date: 2014-03-30
forum: Desktop Environments
---

### Post by Andy_Lawson on 2014-03-30
Hi all,

I started up my Ubuntu 13.10 laptop last night, and found there was no Unity menu available.

The laptop is a Lenovo S430, which has an nVidia GF108M, not sure if that makes any difference. I have installed bumblebee, although I'm not sure if that's the correct thing to do either. Also VirtualBox is installed, which does seem to stuff about with Unity a bit.

I googled and tried a few things, such as;

```
sudo apt-get install compizconfig-settings-manager
export DISPLAY=:0
ccsm
```

Which got me into the Compiz settings config. From here I re-enabled the Unity plugin which has become disabled. Didn't help tho.

I also deleted ~/.config/compiz-1/compizconfigs/config, which may not have been a good idea.

Anybody able to offer insight into this issue?

Thanks!

---

### Post by Andy_Lawson on 2014-03-30
I have no idea how I did it, but it seems to be back.

After a few more reboots, I was able to open a terminal with Ctrl+Alt+T, which I swear didn't work before. I started CCSM and it no longer showed a tickbox next to the Ubuntu Unity plugin. So I clicked the plugin instead, and got into its settings pages. In here was another enable tickbox, which was unticked. So I ticked it. I got a couple or dialogs about clashing shortcuts and then the unity sidebar and system bar came back.

There still there after a reboot, which is nice.

Anybody able to explain what might have happened? I'm still suspicious it'll happen again!

Thanks

---

### Post by grahammechanical on 2014-03-30
Well, well. The ability to disable the Unity plugin from the front page of CCSM was removed more than a year ago. Too may people removing Unity without having an alternative user interface installed and ending up without a user interface.
 
I did not notice that  it had been moved into the Unity plugin settings page. Or perhaps I did not pay attention to it. It is my guess that what you did was the equivalent of doing unity reset or setsid unity as it is more properly called.

How did it become disabled in the first place? Do you have another tweak tool that you have been using?

Regards.

---

### Post by Andy_Lawson on 2014-03-30
Not to my knowledge. I'd been stuffing about with the wireless NIC, but not with the UI.
Hadn't even run updates for ages, because of various reasons. When I got in to the CLI I noticed that a bunch were due, but that was after it broke.

A mystery :(

---

