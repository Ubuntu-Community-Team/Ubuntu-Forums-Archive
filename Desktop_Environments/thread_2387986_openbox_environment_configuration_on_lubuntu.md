---
title: "openbox environment configuration on lubuntu"
date: 2018-03-26
forum: Desktop Environments
---

### Post by charlesubu on 2018-03-26
Hi, 

I didn't find out how to configure openbox `environment` for lubuntu, Could someone share your experience ? 

[TABLE="width: 500"]
[TR]
[TD]Vanilla Openbox[/TD]
[TD]Lubuntu[/TD]
[/TR]
[TR]
[TD].config/openbox/rc.xml[/TD]
[TD] .config/openbox/lubuntu-rc.xml [/TD]
[/TR]
[TR]
[TD].config/openbox/autostart[/TD]
[TD] .config/lxsession/Lubuntu/autostart [/TD]
[/TR]
[TR]
[TD].config/openbox/environment[/TD]
[TD][COLOR=#ff0000] ???[/COLOR][/TD]
[/TR]
[/TABLE]

Thanks.

---

### Post by kerry_s on 2018-03-27
you don't have to do that, there are apps in preferences. openbox is only a part of lxsession.

autostart= preferences-> default applications lxsession-> autostart

anyway it's all in the menu, just have a look around. they try to make it as friendly as possible.

---

### Post by charlesubu on 2018-03-27
Thanks. I was hoping to save all configure files in txt so porting to another computer would be easy.

---

### Post by kerry_s on 2018-03-27
oh okay, you just want to know what are all the files you need to save.
i'll let the lubuntu users help you on that. my memory's not that good. i didn't really fully explore it when i tried it out in vm. i prefer elementary os for a lite linux.

---

