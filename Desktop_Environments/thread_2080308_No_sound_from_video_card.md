---
title: "No sound from video card"
date: 2012-11-03
forum: Desktop Environments
---

### Post by geomcd1949 on 2012-11-03
Ubuntu 12.10 fresh install
HIS iCooler H775F1GD Radeon 7750 1GB 128-bit GDDR5 video card
ASRock Z77 Extreme4 motherboard
Intel Core i7 3770 Ivy Bridge 3.4GHz cpu
ASUS monitor with built-in speakers

Connection from video card to monitor is by HDMI cable.

With video card installed, and HDMI cable from the video-card outlet to  the monitor, no sound is played.  Systems Setting>Sound gives three  options to "Play sound through:" Digital Outout (S/PDIF); Headphones;  and Analog Output. No sound is heard when any of these three are  selected. I can play sound,however, if I connect external speakers by  means of a jack into the Audio Out port on the I/O panel, and select  Analog Output.

If I uninstall the video card, in the Systems Settings>Sound, "Play  sound through," I now get a fourth option listed, HDMI/Display Port 3,  and can play sound by selecting this and connecting the HDMI cable from  the I/O Panel to the monitor.

I suspect this is a video-card driver problem, but not experienced enough to be sure. Advice and guidance greatly appreciated.

~George

---

### Post by geomcd1949 on 2012-11-03
Found the following as I continued to research the problem. It seems the solution might be in the last clause, and I ask if I can get an explanation of what the writer means by "but you can activate it by adding radeon.audio=1 as a [kernel boot parameter]("https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation")."




"As mentioned in an [earlier post]("http://voices.canonical.com/david.henningsson/2011/09/06/pulseaudio-with-jack-detection/"),  much HDMI/DisplayPort hardware have phantom outputs, and there is no  way we know what outputs are real until something is plugged in. With  the new sound settings UI in Ubuntu 12.04, we finally have a good user  experience in this scenario: Only the outputs that are actually plugged  in and possible to activate will be shown.
[IMG]http://voices.canonical.com/david.henningsson/files/2012/04/sound-settings-ui2.png[/IMG]
[SIZE=-1]Sound settings in Ubuntu 12.04[/SIZE]
 **Video drivers**

 Most of the code to activate HDMI/DisplayPort audio is in the video  driver, rather than the audio driver. Therefore, if this is not working,  it is more likely that the problem is within the video driver.
It is also notable that the open source driver for ATI/AMD (called  radeon), has experimental support for HDMI/DisplayPort audio, at least  for some cards. It is [disabled by default]("https://lists.ubuntu.com/archives/kernel-team/2012-February/018898.html"), but you can activate it by adding radeon.audio=1 as a [kernel boot parameter]("https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation")."


Thanks.


~George

---

