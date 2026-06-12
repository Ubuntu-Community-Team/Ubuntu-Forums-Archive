---
title: "HDMI TV White Screen"
date: 2011-11-21
forum: Desktop Environments
---

### Post by amtur_poet on 2011-11-21
I'm trying to set up my old HP Pavilion dv1020-us as a media center, and am hooking it up to a Sony Bravia HDTV, and having it run in 1080p, and the laptop screen running in 1440x990. So, I connected it up to the TV with an HDMI cable, and set up the screens in nvidia-settings to Twinview. But, when I restarted the system, the laptop screen displayed normally, but the TV screen was completely white, and kept flashing out of getting a signal or not. I was able to move my cursor over to the other screen, but I suspect that only the X server started, because the cursor was a black "X". Then, I checked nvidia-settings, and saw that it has swtiched to "Seperate X Screen", as opposed to Twinview. I tried activating Twinview, but my laptop screen went black,except for the cursor, and the TV screen remained white. What can I do to fix this? I don't need to have Twinview, either; I just need the TV screen to work. The laptop screen can be disabled if necessary. Any ideas?

Also, when I try to disable the laptop screen in favor of the TV, it gives me the following error: "Failed to set MetaMode (1) 'DFP-1: nvidia-auto-select @1920x1080 +0+0' (Mode 1920x1080, id: 155) on X screen 1."

---

### Post by amtur_poet on 2011-11-22
Please help, guys!

---

### Post by amtur_poet on 2011-11-22
...Anybody?

---

### Post by amtur_poet on 2011-11-23
Ugh, I can never get any help on these forums. I tried the same setup with a VGA cable, and it gave me the same error. I was able to enable Twinview briefly, but the TV just showed a mess of scrambled lines of the correct display, and the laptop screen just showed a purple stripe on a black background.

EDIT: Also, enabling Twinview only "works" once in a great while. most of the time, I get this error:

Failed to set MetaMode (1) 'DFP-0: 1440x900_60 @1440x900 +0+0, CRT-0: 1920x1080_60 @1920x1080 +1440+0' (Mode 3360x1080, id: 51) on X screen 0.

---

