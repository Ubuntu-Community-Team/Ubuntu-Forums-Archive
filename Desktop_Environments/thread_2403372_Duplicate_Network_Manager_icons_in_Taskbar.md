---
title: "Duplicate Network Manager icons in Taskbar"
date: 2018-10-10
forum: Desktop Environments
---

### Post by MoebusNet on 2018-10-10
The duplicate icon most often appears after a reboot; not usually present from a cold boot. However a Software Update can cause the duplicate icon to appear. Searching for a solution, I tried: ```
 sudo leafpad ~/.config/lxpanel/Lubuntu/panels/panel 
``` and changed 'network=0' to 'network=1' at the advice of a thread at linuxquestions.org for Lubuntu 17.10. This hasn't worked for me. Any advice on what to do about this? The duplicate icon does not have the Network Manager menu attached to it, only the original does. I haven't figured out how to remove the duplicate without screwing up the original.

---

### Post by MoebusNet on 2018-10-12
I was hoping for a proper fix, but as a workaround, In Lubuntu 18.04 I have deleted 'Indicator Applets' (Right-Click Network Manager Icon then Add/Remove Panel Items>Remove "Network Manager" From Panel). This removes both the duplicate Network Manager icon and the Volume Control icon from the task bar. Next, Right-Click the taskbar and add the Volume Control back (Add/Remove Panel Items>Add>Volume Control) then select Volume Control and use Up/Down to place Volume Control icon properly on the taskbar. I guess with LXDE being replaced in Lubuntu, this may not get a fix.

---

