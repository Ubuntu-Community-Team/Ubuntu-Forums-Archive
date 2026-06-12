---
title: "Another visual effects help thread"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by CarnivorouZ on 2008-02-26
I have read every page I could on fixing my visual effects so that I am able to enable desktop effects but have been unsuccessful so far. When I enable the restricted AIT driver, it sends me to a black screen upon reload.  After the Ubuntu load screen it goes straight to black without going to the Gnome desktop.
I have enabled Compiz and fglrx.  I have tried adjusting my resolution to 1024x768.  
Here is my current xorg setup:

code:
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc ATI Default Card"
Monitor "SyncMaster"
DefaultDepth 24
SubSection "Display"
Modes "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

The video card is a ATI Radeon x1650.
Please Let me know if there is any other info I can provide to help me solve this issue. I would really like to utilize Ubuntu's visual effects.
__________________

---

### Post by Ub1476 on 2008-02-26
If the drivers does not work after a restart (Ubuntu configures them automatic for you), you can use the latest drivers from ATI. They are quite fine by now, but I suggest you follow [this]("http://forum.compiz-fusion.org/showthread.php?t=6794") thread to gain better performance. 

[Envy]("http://albertomilone.com/nvidia_scripts1.html") is a very good script which will download those drivers and configure them for you, availble in both GUI and text-mode. Make sure you remove the current installed driver first and XGL (which wont be needed).

Oh and, to configure Compiz-Fusion (visual effects), you need to install Advanced Desktop Effects, available in repos.

---

