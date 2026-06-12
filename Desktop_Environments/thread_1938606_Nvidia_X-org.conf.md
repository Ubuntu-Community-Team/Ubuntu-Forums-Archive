---
title: "Nvidia X-org.conf"
date: 2012-03-10
forum: Desktop Environments
---

### Post by shashanksingh on 2012-03-10
Hi.
I have an nvidia 520 geforce card.

I use an HDMI cable and the nvidia Xserver settings detects my Samsung TV and a CRT, for the HDMI cable and the VGA respectively I suppose.

The appropriate resolution for my monitor is 1360x768.

When I tell it to apply, it applies the same. But the first time I told it to save to configuration file, it gave me some error in parsing the configuration file.

I have attatched the file before and after. Also, although the resolution in the file is 1360x768, the login screen comes in that resolution, but after that it drops down to 1024x768.
:(

---

### Post by Zorael on 2012-03-10
The second xorg.conf looks pretty borked, yes. :> But (as you point out yourself) overall I think the nvidia driver is smart enough nowadays to apply the best possible resolution upon X start even if they're not defined there in the configuration file.

To wipe your user-specific configuration (which is getting applied and changing your resolution upon logging in) and start anew completely, remove the **~/.nvidia-settings-rc** file. Moreover there's also the chance that your desktop environment -- which I assume is GNOME/Unity as you tagged your thread with **[COLOR="DarkOrange"][ubuntu][/COLOR]** -- is also reading its own saved resolution settings and applying those. Hopefully wiping the nvidia-settings configuration will be enough to clear any user-specific bits.

Is that what you want to achieve? To simply let it keep the resolution it automatically uses at the login screen and not lower it once you log in?

---

### Post by shashanksingh on 2012-03-11
> **Zorael said:**
> The second xorg.conf looks pretty borked, yes. :> But (as you point out yourself) overall I think the nvidia driver is smart enough nowadays to apply the best possible resolution upon X start even if they're not defined there in the configuration file.

To wipe your user-specific configuration (which is getting applied and changing your resolution upon logging in) and start anew completely, remove the **~/.nvidia-settings-rc** file. Moreover there's also the chance that your desktop environment -- which I assume is GNOME/Unity as you tagged your thread with **[COLOR="DarkOrange"][ubuntu][/COLOR]** -- is also reading its own saved resolution settings and applying those. Hopefully wiping the nvidia-settings configuration will be enough to clear any user-specific bits.

Is that what you want to achieve? To simply let it keep the resolution it automatically uses at the login screen and not lower it once you log in?

You were right, after a fresh install and update in my system(disk errors could not be repaired :P), it automatically does it, and my xorg is very very simple now. it used to detect 1024x768 as default although I had saved it as 1360x768, but it automatically worked fine on a fresh install. Thanks :)

---

