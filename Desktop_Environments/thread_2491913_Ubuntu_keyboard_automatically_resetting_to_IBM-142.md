---
title: "Ubuntu keyboard automatically resetting to IBM-142"
date: 2023-10-25
forum: Desktop Environments
---

### Post by francesco.grassell on 2023-10-25
Hi everyone, I have a problem with the keyboard settings of Ubuntu Studio 22 (Plasma). I configured the keyboard as "generic 105 key" and the mapping as "Italian (Windows)" but it always defaults to "Italian (IBM 142) " and I can't get it off in any way. I tried removing it from the Keyboard - Configure mappings menu, leaving only the Windows mapping, but it always switches back to the IBM 142 mapping. I tried with the command
```
sudo dpkg-reconfigure keyboard-configuration
```
But nothing changed.
The keyboard configuration files is as follows:
```
# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="it"
XKBVARIANT="winkeys"
XKBOPTIONS="lv3:ralt_switch,terminate:ctrl_alt_bksp"

BACKSPACE="guess"
```
As for now, the only thing I have been able to do is configuring the Alt+Shift command to switch to Windows keyboard mapping when I need it, but it is still a hassle... any other ideas? 
Thank you in advance

---

