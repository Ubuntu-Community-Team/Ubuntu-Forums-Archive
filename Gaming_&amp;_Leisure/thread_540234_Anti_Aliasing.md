---
title: "Anti Aliasing"
date: 2007-09-01
forum: Gaming &amp; Leisure
---

### Post by RudolfMDLT on 2007-09-01
Hi there,

Did any of the Linux gamers get Anti Aliasing to work in their games? I'm pretty much new to Wine and games in Ubuntu and I've managed to get everything except Anti Aliasing to work? 

Thanks,

Rudolf

---

### Post by cogadh on 2007-09-01
Most of the time, the only way I can get AA to work is by using the Nvidia config utility and setting it globally.

---

### Post by RudolfMDLT on 2007-09-02
Nvidia Config Utility?

I think I had that installed when I once used the Envy script, but now I'm just running the stock proprietary driver that Ubuntu driver manager installed... What Nvidia driver are you running?

Thanks,

Rudolf

---

### Post by Sockerdrickan on 2007-09-02
I got it working with DOOM 3

---

### Post by cogadh on 2007-09-02
> **RudolfMDLT said:**
> Nvidia Config Utility?

I think I had that installed when I once used the Envy script, but now I'm just running the stock proprietary driver that Ubuntu driver manager installed... What Nvidia driver are you running?

Thanks,

Rudolf
I use the nvidia-glx-new package, but I believe the config utility is also included with the standard nvidia-glx package. Just run "nvidia-settings" in a terminal, it should launch the utility.

---

### Post by Sockerdrickan on 2007-09-02
sudo nvidia-settings saves them for next x boot

---

### Post by cogadh on 2007-09-02
**Never** run nvidia-settings with sudo or as root, it is very bad. If you run it as a normal user, it saves the settings in your home directory as a hidden file and it loads it when you run the settings app. That way, each user gets their own custom Nvidia profile. If you want the Nvidia settings to load at each log in, then edit your xinitrc and add the line "nvidia-settings --load-config-only" to it.

---

### Post by RudolfMDLT on 2007-09-04
:) Thanks! enabled anti aliasing, I didn't get the option to enable it in the game and my frame rate actually dropped! :) Ahwell! :)

Thanks for the advice everybody!

---

### Post by Sockerdrickan on 2007-09-04
> **cogadh said:**
> **Never** run nvidia-settings with sudo or as root, it is very bad. If you run it as a normal user, it saves the settings in your home directory as a hidden file and it loads it when you run the settings app. That way, each user gets their own custom Nvidia profile. If you want the Nvidia settings to load at each log in, then edit your xinitrc and add the line "nvidia-settings --load-config-only" to it.
What is bad with it?

---

### Post by Elohim on 2007-09-04
> **Tux0r said:**
> What is bad with it?

It's probably bad if you have multiple folks using the same box, but if you're like most people here and using it on your own box, then it probably doesn't matter if you run it as root :)

---

### Post by cogadh on 2007-09-04
Honestly, I don't remember why it would be bad. I think when the settings app was first added to the Nvidia driver installation, the instructions said don't use root to run it. That may have changed since the initial release, I just have built up the habit of only using it as normal user and editing xinitrc to load the settings. I do have a multi-user system and it definitely works better that way for my situation.

---

### Post by Sockerdrickan on 2007-09-04
> **Elohim said:**
> It's probably bad if you have multiple folks using the same box, but if you're like most people here and using it on your own box, then it probably doesn't matter if you run it as root :)
Yeah I know, everyone is over reacting with this **VERY** serious tone when someone says sudo...

---

### Post by MaximB on 2007-09-05
For those who have ATI video card like me it's very easy.
go to the ATI Catalyst control center (after you have installed the AMD/ATI drivers).
in the bottom, there is a 3d section, there you can set the anti-alising and  anistropic, set them and restart the PC, after this you must set it in-game too.

---

### Post by derekr44 on 2007-09-05
I've got 4xAA running on WoW.

---

