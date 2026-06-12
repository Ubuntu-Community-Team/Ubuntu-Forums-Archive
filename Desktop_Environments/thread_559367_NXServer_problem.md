---
title: "NXServer problem"
date: 2007-09-25
forum: Desktop Environments
---

### Post by AdamKlob on 2007-09-25
I'm using Gutsy Gibbon and I have strange problem with NX.

I have both KDE and Gnome installed. When I'm using my machine locally I use Gnome. Unfortunetly,under NX Gnome, and any GTK based applications are not visible. They start (ps shows that) but they do not show on NXClient. They do not appear on local desktop either (checked with VNC).

It worked for some time, but after some of gutsy recent updates, it does not work anymore.

Here is NXserver log:

Sep 25 09:39:46 adamk NXSERVER-3.0.0-63[29282]: User 'adamk' logged in from '83.12.226.166'. 'NXLogin::set'
Sep 25 09:39:48 adamk NXSERVER-3.0.0-63[29282]: Selected node host:localhost with port:443 'main::selectNode'
Sep 25 09:39:48 adamk NXSERVER-3.0.0-63[29282]: Current selected node: localhost is in status: running  'main::selectNode'
Sep 25 09:39:49 adamk NXSERVER-3.0.0-63[29282]: Selected session type: unix-gnome allowed in the profile of user: adamk 'NXShell::Static'
Sep 25 09:39:52 adamk NXSERVER-3.0.0-63[29282]: Session '6B06B347C70288060B96C7BDE8A77F4E' started by user 'adamk'. 'NXShell::handler_session_start'
Sep 25 09:39:52 adamk NXNODE-3.0.0-76[29298]: Using port '1046' on node 'adamk' for session 'unix-gnome'. Logger::log nxnode 5733
Sep 25 09:39:52 adamk NXNODE-3.0.0-76[29298]: Using host from available host list: '87.105.104.21'. Logger::log nxnode 5734
Sep 25 09:39:52 adamk NXSERVER-3.0.0-63[29282]: User 'adamk' from '83.12.226.166' logged out. 'NXLogin::reset'

(sometimes when I try to use NX I se panels and wallpaper (but no icons), Ubuntu menu works, but I still do not see any GTK application, on other cases I see only black screen, this log is from black screen case)

---

