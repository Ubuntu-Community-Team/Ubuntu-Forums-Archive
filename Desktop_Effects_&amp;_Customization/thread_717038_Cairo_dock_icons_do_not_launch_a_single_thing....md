---
title: "Cairo dock icons do not launch a single thing..."
date: 2008-03-06
forum: Desktop Effects &amp; Customization
---

### Post by larryfroot on 2008-03-06
Hi

Have just updated my cairo-dock....quit it and opened it up again from the terminal....where I was presented with this cheerful message...

rsvg_handle_get_dimensions: assertion `handle' failed
rsvg_handle_render_cairo_sub: assertion `handle != NULL' failed
warning :  (cairo-dock-keyfile-manager.c:cairo_dock_replace_key_values:177)  
  Attention : Key file does not have key 'frame_file'

...and now although Cairo Dock performs the parabola and other tricks beautifully, the icons do not launch a single thing. Except the trash can for some unknown reason.

If anyone out there knows anything, this could be a humane time to share it. Thank you! I suppose its all part of being an eye-candy junkie. Like crack, only less sociable.

---

### Post by kbless7 on 2008-03-06
Did you check the commands for the launchers? Many times they put the wrong command in so it doesn't launch.

---

### Post by larryfroot on 2008-03-07
Hi,

Thanks for your reply....I have just checked the launcher icons - as well as the applets - the launch commands are sat there, where they should be...its a case of initialising the things as the icons do not go into their cute animations whilst the app that they have launched starts up. I am going to check - or at least poke around the trash icon/config, as that still works. Bizarre. Puzzling.

Aha...sorted it eventually...the new dock configuration didn't pick up on the launcher commands...a simple matter of replacing the old launchers with new ones...duhhh...thick as s.... sometimes.

---

### Post by phamdt8 on 2008-04-04
i have the same problem. i found out if you remove the value for "Base URI" for all launchers under ~/.cairo-dock/current_theme/launchers then it's will work. Maybe set "Is URI=false" also work.

anyway set to nothing
Base URI=

---

