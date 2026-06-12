---
title: "unhide_delay for top panel not working."
date: 2011-07-20
forum: Desktop Environments
---

### Post by cwhittier on 2011-07-20
I need to disable all access to anything except my application that is set to launch on start-up. I have seen this referred to as kiosk setup. I have written a script to do this. I need to keep gnome-panel running, because it seems if I don't then USB drivers will not show up in the /media folder which my application relies on. 

I am using these commands:


#delete bottom panel (can't delete both, or else they will reset)
gconftool -s -t list --list-type string /apps/panel/general/toplevel_id_list [top_panel_screen0]

#Hide Top Panel
gconftool --set -t bool /apps/panel/toplevels/top_panel_screen0/auto_hide true
gconftool --set -t int /apps/panel/toplevels/top_panel_screen0/unhide_delay 2147483646
gconftool --set -t int /apps/panel/toplevels/top_panel_screen0/auto_hide_size 0

#Turn Off Desktop
gconftool --set -t bool /apps/nautilus/preferences/show_desktop false

#Disable 2nd Desktop
gconftool --set -t int /apps/metacity/general/num_workspaces 1


I also have reset using the following code, to make sure I didn't fudge some setting while experimenting:

gconftool --recursive-unset /apps/panel
pkill gnome-panel

Can anyone tell me why it might not be working, or suggest a better way to eliminate all the panels without losing the automount to the /media folder?

P.S. I am running Ubuntu 9.04 - upgrading is not a possible solution in this instance.

---

### Post by cwhittier on 2011-07-26
After no replies here, and further research, I found a solution that worked for me, however it was slightly complex.

The problem lies in nautilus ending it's process because it sees there  are no windows to be drawn. (the desktop counts as a window) This means that USB drive insertion will not  be detected.

The solution I used can be found here. It involves creating scripts and  rules, and using udev to the detection and mounting. If you are just  having trouble getting automount to work, and you have not intentionally  stopped nautilus from running, this is probably NOT the solution to  your issue.

[http://superuser.com/questions/53978...t-without-a-us]("http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us")

---

### Post by cwhittier on 2011-07-26
P.S. This was a solution for my original intent, removing gnome-panel without sacrificing automount. I've removed gnome-panel completely, so I no longer have a need to set an unhide-delay, however I still do not know why this setting was not working.

---

