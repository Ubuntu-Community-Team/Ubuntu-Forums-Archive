---
title: "How to remove some speakers from Settings-&gt;Sound"
date: 2022-06-14
forum: Desktop Environments
---

### Post by johnaaronrose on 2022-06-14
On Settings->Sound, there are a number of Output Devices which  don't work e.g. Analogue Output - Built-in Audio. When I reboot / log in  the first in the list is always selected. Can I move the one which  works (Line Out - ...) to be the default or remove the non-working ones  from the list?
Here is some Terminal output that might be useful:
> $ pactl list short sinks
1   alsa_output.usb-C-Media_Electronics_Inc._USB_Audio_Device-00.analog-stereo  module-alsa-card.c  s16le 2ch 44100Hz   RUNNING
2   alsa_output.pci-0000_09_00.4.analog-stereo  module-alsa-card.c  s16le 2ch 44100Hz   IDLE
7   alsa_output.pci-0000_07_00.1.hdmi-stereo    module-alsa-card.c  s16le 2ch 44100Hz   SUSPENDED

---

### Post by TheFu on 2022-06-14
Yes, you can.
Perhaps you'd like to set the default to a specific choice?  pacmd can do this.

Or you can disable the non-working devices using pavucontrol - the far right-tab.  Start there and work left through each tab.

---

### Post by johnaaronrose on 2022-06-14
pavucontrol shows a device (Built-in Audio) which I set to Off on its profile: it now no longer shows on the OutputDevices in pavucontrol. Is that the correct thing to do, given that Settings->Sound still shows it after exiting Settings and starting it again.?
pacmd has an option to list-sinks. I don't know what to do after that.

---

