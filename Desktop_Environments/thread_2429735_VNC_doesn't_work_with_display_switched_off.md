---
title: "VNC doesn't work with display switched off"
date: 2019-10-22
forum: Desktop Environments
---

### Post by jklarson on 2019-10-22
I have my Ubuntu 19.10 HTPC plugged-in to a HDMI switch, which then  routes to my monitor. Most of the time that HDMI switch is set to my  Nvidia ShieldTV streaming device and the TV is off.

  When I VNC into my HTPC I am usually unable to do *anything* on  the screen. Mouse and keyboard inputs through VNC are completely  ignored. Nothing software fixes this including systemctl restart gdm. Looking through syslog, I found a "monitor is undefined" error.

  ```
Oct 21 15:37:30 myhost gnome-shell[1119]: JS ERROR: Extension dash-to-panel@jderose9.github.com: TypeError: monitor is undefined#012checkIfFocusedMonitor@/home/myuser/.local/share/gnome-shell/extensions/dash-to-panel@jderose9.github.com/panelManager.js:266:9#012_adjustForOverview@/home/myuser/.local/share/gnome-shell/extensions/dash-to-panel@jderose9.github.com/panel.js:429:32#012enable@/home/myuser/.local/share/gnome-shell/extensions/dash-to-panel@jderose9.github.com/panel.js:112:9#012enable@/home/myuser/.local/share/gnome-shell/extensions/dash-to-panel@jderose9.github.com/panelManager.js:72:9#012_enable@/home/myuser/.local/share/gnome-shell/extensions/dash-to-panel@jderose9.github.com/extension.js:91:5#012enable@/home/myuser/.local/share/gnome-shell/extensions/dash-to-panel@jderose9.github.com/extension.js:63:5#012_callExtensionEnable@resource:///org/gnome/shell/ui/extensionSystem.js:132:13#012loadExtension@resource:///org/gnome/shell/ui/extensionSystem.js:264:21#012_loadExtensions/<@resource:///org/gnome/shell/ui/extensionSystem.js:482:13#012collectFromDatadirs@resource:///org/gnome/shell/misc/fileUtils.js:27:17#012_loadExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:457:9#012_enableAllExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:491:13#012_sessionUpdated@resource:///org/gnome/shell/ui/extensionSystem.js:522:13#012init@resource:///org/gnome/shell/ui/extensionSystem.js:32:9#012_initializeUI@resource:///org/gnome/shell/ui/main.js:245:5#012start@resource:///org/gnome/shell/ui/main.js:141:5#012@<main>:1:31
```

  Sure enough, when I turned the TV on everything immediately starts to  work. From my research, I found this question below which addresses running Ubuntu headless.

  [URL="https://askubuntu.com/questions/1033436/how-to-use-ubuntu-18-04-on-vnc-without-display-attached"]How to use Ubuntu 18.04 on VNC without display attached?
[/URL]
  However I am *not* running headless, I have a monitor attached, it's just turned off. Any way to make this work at the X/Gnome level? 
  Additionally I tried disabling all Gnome extensions entirely in the  tweak tool and the problem still happened. So this is not an extension  problem.

---

### Post by sailingboyLLB on 2019-11-16
I leave my HTPC hooked up to my TV and don't have this problem. I suspect the switch is the issue, not the fact that the monitor is turned off. At an electrical level a display connected via HDMI is still detectable even if the display is off. If the connection is not made because the cable is unplugged or the switch effectively makes the cable unplugged then you are effectively headless and all those suggestion solutions apply: dummy resistor display connected, software dummy display, etc. Could you hook the computer to another input on the monitor instead of the switch? even if you used a DVI adapter for example?

---

