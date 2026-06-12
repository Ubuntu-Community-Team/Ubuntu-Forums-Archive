---
title: "Ubuntu 14.04, Xfce switching workspace using mouse"
date: 2014-06-25
forum: Desktop Environments
---

### Post by mctiew on 2014-06-25
I find it rather annoying to have to use keyboard ctrl+alt+left and ctrl+alt+right to switch workspace.

I would like to do everything from mouse. But using the window manager tweaks-->workspaces-->mouse wheel scroll isn't satisfactory either, as it switches workspaces but sometimes it switches more than one. I feel a bit lost which I can't know for sure which workspace I go to.

So finally I installed this tool, 'xdotool' to do this :-

nohup xdotool behave_screen_edge --delay 250 bottom-right key ctrl+alt+Right >/dev/null 2>&1 &
nohup xdotool behave_screen_edge --delay 250 bottom-left key ctrl+alt+Left >/dev/null 2>&1 &

The delay has no meaning since I only need to hit one set of key, one time. Maybe it should be removed.

I put these into a scripts called 'screen_trigger.sh' and make it autorun :-

$ cat ~/.config/autostart/edgetrigger.desktop

[Desktop Entry]
Name=XDO Screen Edge Trigger
GenericName=Screen Edge
Comment=Sets screen trigger
Exec=/home/mctiew/screen_trigger.sh
Terminal=false
Type=Application
Icon=input-mouse
X-GNOME-Autostart-enabled=true

Now when I moved the mouse to the bottom right and bottom left, it switches one workspace to the right and left.

---

