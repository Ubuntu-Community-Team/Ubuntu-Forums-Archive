---
title: "Move close,min,max buttons in gnome classic"
date: 2012-07-06
forum: Desktop Environments
---

### Post by ksteuber on 2012-07-06
I just installed Ubuntu desktop 12.04 on my laptop and Ubuntu server 12.04 on my desktop. I like gnome classic, so I am using it on both boxes. However, on my laptop, the close, min and max buttons are on the left side of the windows while on my desktop they are on the right side. I don't really care which side they are on, but I would like them to be the same.

I have already searched for this problem a fair amount and found these solutions:
1) Use gconf-editor to change the location of the colon in /desktop/gnome/shell/windows/button_layout
2) Use gconf-editor to change the location of the colon in /apps/metacity/general/button_layout
3) Use dconf-editor to change the location of the colon in /org/gnome/shell/overrides/button_layout

None of these solutions have worked for me. Can anyone else offer any others?

---

### Post by Karlchen on 2012-07-06
Hello, ksteuber.

The following worked for my Ubuntu 12.04 installation and moved back the minimize, maximize and close icons to the right side of the application windows:

[LIST]
[*]installed gconf-editor with the help of synaptic
[*]launched gconf-editor
[*]went to apps => metacity => general
[*]changed the value of "button_layout" to read "menu:minimize,maximize,close"
[/LIST]
Basically these steps read like item (2) on your list provided you have changed the value of button_layout to exactly the right string (see above) Else your change may simply have been ignored.

Hm, I see you are on Gnome Classic. As a matter of fact I am on Unity right now. But for me the given steps have worked as expected in every Gnome based Ubuntu version since Lucid Lynx. So I do not see why they should fail on Gnome Classic. (But who knows?!)

HTH,
Karl

---

### Post by dcsoldschool53 on 2012-07-07
**You can also change the position of the close, min, max, buttons using Ubuntu-Tweak. I hope this helps.:p**

---

### Post by kansasnoob on 2012-07-07
Buttons to the right:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

Buttons to the left:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```

---

