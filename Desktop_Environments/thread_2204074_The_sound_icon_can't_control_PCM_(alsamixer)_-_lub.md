---
title: "The sound icon can't control PCM (alsamixer) - lubuntu-rc.xml"
date: 2014-02-06
forum: Desktop Environments
---

### Post by TalkinJive on 2014-02-06
Good evening,
The sound icon of LXDE desktop controls "MASTER" of alsamixer. But it's useless because it's the "PCM" that controls the sound level.
So I try to configure the sound icon to control "PCM" instead of "MASTER".
I change **/home/xuser/.config/openbox/lubuntu-rc.xml** :
The lines 
[FONT=courier new]<command>amixer -q sset Master 3%+ unmute</command>[/FONT]
[FONT=courier new]<command>amixer -q sset Master 3%- unmute</command>[/FONT]
[FONT=courier new]<command>amixer -q sset Master toggle</command>[/FONT]
become
[FONT=courier new]<command>amixer -q sset PCM 3%+ unmute</command>[/FONT]
[FONT=courier new]<command>amixer -q sset PCM 3%- unmute</command>[/FONT]
[FONT=courier new]<command>amixer -q sset PCM toggle</command>[/FONT]

I reboot. But no way ! The icon still controls "MASTER" of alsamixer ! :-(
I try the line "[FONT=courier new]amixer -q sset PCM 3%- unmute" (for exemple) [FONT=arial]in a Terminal and it works.
So can I guess that lubuntu-rc.xml is useless ?
Please could you tell me how I can configure the sound icon to control "PCM" instead of "MASTER".
Thanx for your help !
Gérald.[/FONT][/FONT]

---

### Post by walterorlin on 2014-02-06
After editing that file you will need to run ```
openbox --reconfigure
``` in a terminal as it is still using old configuration have You done that? Then it should work.

---

### Post by TalkinJive on 2014-02-08
Hello walterorlin

I thanx you for the response.
I didn't reconfigure openbox. I try it but infortunetly it doesn't work. The sound icon stills control the "MASTER" instead of "PCM".
Notice that I find two similar files (I think the first is the pattern. It may be installed in /home)
/usr/share/lubuntu/openbox/rc.xml
/home/userx/.config/openbox/lubuntu-rc.xml
I try to configure the 2 files before "[COLOR=#000000][FONT=Ubuntu Mono]openbox --reconfigure[/FONT][/COLOR]" but no way.

Have you got another idea ?
Thanx.

---

### Post by walterorlin on 2014-02-19
There is a way to open alsamixer throught right clicking on the speaker and then clicking sound settings and do that in alsamixer.

---

