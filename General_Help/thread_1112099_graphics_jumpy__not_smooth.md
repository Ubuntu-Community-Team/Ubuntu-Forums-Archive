---
title: "graphics jumpy / not smooth"
date: 2009-03-31
forum: General Help
---

### Post by VCoolio on 2009-03-31
Conky screws my graphics up. My mouse and video playback stopped working smooth. Every one or two seconds there is a jump. This entry seems to be the problem:
${color}Keyboard: ${color}${execi 1 setxkbmap -v 7 | grep layout | awk '{print $2}'}

It checks for my keyboard layout. I switch a lot between classical greek and us. Now what could be the problem? If I set execi 10 the jumps slow down, but are still there. Some other entries:

background yes
update_interval 2.0
own_window yes
own_window_type normal # 'normal' or 'override' or 'desktop'
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
no_buffers yes # what does this do??

FYI: running an up-to-date intrepid + compiz, GeForce FX 5200 with nvidia driver 173.14.12. Forget the replies 2-5, they were from before I discovered that conky was the problem. I re-edited this first post accordingly.

---

### Post by James_Lochhead on 2009-03-31
Try updating to a new driver anyway. That is not the newest one. You can get 177 on Intrepid.

---

### Post by VCoolio on 2009-03-31
Ok, thanks for your reply. I tried that with synaptic. After rebooting I could only use low graphic mode. Checked this forum and concluded that changing drivers equals entering hell. Also yesterday this very driver did fine. So I'm back now with my old driver and the problem stands.

---

### Post by James_Lochhead on 2009-03-31
Hmm it should not actually cause many problems: that is the whole point of the driver in the repositories.

The driver on the NVidia site is another matter... that will break every time you update your kernel.

If you are having problems with the new driver just drop to a failsafe terminal in GDM and type sudo nvidia-xconfig

---

### Post by VCoolio on 2009-03-31
tnx for your very fast replying. I googled my videocard in combination with the 177 driver and I am not sure if the two are compatible; check the comment at the end of the page [here]("http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-8.10-nvidia"), or the title of this [bug]("https://bugs.launchpad.net/bugs/263528").

Also I'm still not sure what problem I now have that this new driver would fix.

EDIT: wow, this is very weird. I killed conky (which I have running for a week) and the problem disappears! This is the first time in one and a half year that I have such a MS-like experience with Ubuntu. So this narrows it down. Now I need the solution.

---

