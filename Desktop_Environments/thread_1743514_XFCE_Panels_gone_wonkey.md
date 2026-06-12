---
title: "XFCE Panels gone wonkey"
date: 2011-04-29
forum: Desktop Environments
---

### Post by ciaopaulo on 2011-04-29
Hi all,

So thanks to some obscure and slightly buggy options in the xfce settings I've now got an xfce panel that consists of an empty box.

Closing and restarting xfce4-panel doesn't change anything, the box just disappears and reappears.

How can I get the panel back how it should be, at the bottom (or top) of the screen, showing all the usual icons?

Install is Xubuntu 10.10 x386

Cheers,

Paul

---

### Post by 3Miro on 2011-04-29
Right-click on the panel should bring up options and you should be able to specify the position for the panel. If not, then you can use the Apps -> Settings -> Settings Manager -> Panel.

You can then right-click on the panel and select "add". You can add all the applets that you want in whatever order that you want.

---

### Post by ciaopaulo on 2011-04-29
OK thanks for that. I set the panel to fixed, bottom, full width. Now I have an empty panel.

I've added a few items but these aren't the same as before.

Isn't there a quick and easy way to get all the default items that were there on install?

---

### Post by ciaopaulo on 2011-04-29
OK I've got it.

sudo mv ~/.config/xfce4/panel tmp/

where tmp is just a dump directory)

will force xfce to create a new xml file containing all the config data.

I'm sure there's a copy of the default files somewhere but I couldn't find them.

---

