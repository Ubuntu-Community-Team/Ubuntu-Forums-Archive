---
title: "How do I lock the screen in XFCE?"
date: 2008-12-25
forum: Desktop Environments
---

### Post by JordyD on 2008-12-25
How do I lock the screen in XFCE?

Usually I use Ubuntu, and whenever I walk away from my computer, I ctrl+alt+l. But I noticed on my laptop that runs Xubuntu, I can't do that.

Is there a key combination or button I can press?

Thanks,
Jordy

---

### Post by lipwig on 2009-01-26
I'm having that same problem. I have added the 'lock screen' action button, which works fine, and my screen is also set to lock once my screen saver loads, but I'm just use to being able to ctrl+alt+l and lock it. Any suggestions would be very much appreciated.

---

### Post by Denestria on 2009-01-26
Open the settings manager > keyboard > shortcuts and you can see that the default shortcut to lock the screen is ctrl-alt-del.  If you want to change it, click add on the left, type in a name for your list of shortcuts, (widen the window so you can see the whole thing) select xflock4 shortcut on the right and enter the new key combo.

---

### Post by adamlau on 2009-01-26
Or simply run:

```
xflock4
```

---

### Post by lipwig on 2009-01-28
Thanks! Problem solved.

---

### Post by chika.tambun on 2009-04-29
alternative way...
create icon shortcut on the upper panel by:
1. right click on the panel
2. choose add new items
3. choose action buttons
4. select action type >> Lock
5. nice icon created


ym_id: chika.tambun
"someone that used to use gnome, but recently 'ev impressed with kde, but choose xfce for stability n lightness on jaunty"

---

### Post by bagy on 2009-10-06
Press Ctrl+Alt+Delete

---

### Post by candida on 2010-09-15
thanks for pointing me in the right direction, in my case however it was already configured in keybord settings correctly to point to /usr/bin/xflock4, but when trying that out on the command line some dependecy were missing: /usr/bin/xlock
where after i had to install xlockmore to obtain the missing executable. It was on a opensuse 11.3 system, i've never got this type of issue on my xubuntu partition..

---

### Post by berlinick on 2011-08-28
My case is quite funny:

[LIST]
[*]I have an action button, which isn't (always) working
[*]In my Settings Manager the keyboard shortcut is set at Ctrl+Alt+Del for xflock4 but the system just doesn't react on the combination
[*]Running xflock4 in Terminal returns "xscreensaver-command: already locked."
[/LIST]

There must be some conflict or something somewhere. I will very much appreciate your suggestions :)

Best wishes

---

### Post by jringoot on 2012-04-03
Thanks Denestria, clear and concise. 
Works also in  Sabayon Linux.

---

