---
title: "XKBOPTIONS=&quot;numpad:microsoft&quot; not working"
date: 2014-07-22
forum: Desktop Environments
---

### Post by freemant on 2014-07-22
Hi,

I am using ubuntu with the lubuntu desktop installed. I am trying to get the keypad to behavior properly (e.g., shift arrow remaining as shift arrow) by setting XKBOPTIONS="numpad:microsoft" in /etc/default/keyboard. However, it seems to have no effect. It is indeed being picked as seen from the /var/log/Xorg.0.log file:

[    33.900] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.900] (**) Option "xkb_rules" "evdev"
[    33.900] (**) Option "xkb_model" "pc105"
[    33.900] (**) Option "xkb_layout" "us"
[    33.900] (**) Option "xkb_options" "numpad:microsoft"

I am using 12.04 (newly upgraded). Any idea? thanks!

---

