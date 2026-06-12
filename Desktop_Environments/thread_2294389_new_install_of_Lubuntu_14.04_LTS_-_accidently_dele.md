---
title: "new install of Lubuntu 14.04 LTS - accidently deleted key items in LXPanel"
date: 2015-09-10
forum: Desktop Environments
---

### Post by bowie101 on 2015-09-10
Hello. After installing Lubuntu 14.04 LTS, I deleted some key things in the LX PAnel that I would like/need back. Like, the main application launcher (the menu button?) that has all the applications arranged by category. And then I have yet to get network manager's wireless indicators to actually accept the security password that I type in . So effectively, no wifi is working, except possibly at the location where I originally installed the OS. Is there an easy way to a) get things back to the default state on the desktop and b) improve the wifi to the point that it actually works? And then works intuitively ? 

Too little sleep is my problem right now. Will sleep now to fight another linux day. 

Thanks, B.

---

### Post by Sunil_Daswani on 2015-09-11
[https://www.google.co.in/search?q=+LX+PAnel+sudo&ie=utf-8&oe=utf-8&gws_rd=cr&ei=_4fyVa7sHoOyuQT41ZrIAw](https://www.google.co.in/search?q=+LX+PAnel+sudo&ie=utf-8&oe=utf-8&gws_rd=cr&ei=_4fyVa7sHoOyuQT41ZrIAw)



should work. also if u find the apps in the sudo program.. should work as well.


~sun

---

### Post by bowie101 on 2015-09-11
OK! Sleep does wonders! Yes, I seemed to have solved it. Not exactly back to what I remember seeing before, but I'll take what I got, and who knows, it's probably just the style that's different. I solved this by using aptitude and the software center to completely remove and then reinstall everything to do with the lxpanel and whatever else it brought up (some lubuntu desktop core packages). The computer seemed to hang during the reinstallation, but I left it on and went to bed. Woke up, the battery was dead, so I plugged it in, turned it on, and things look different, with a new taskbar, so this is progress. Thanks! Now my only issue is with this nm-applet not working with wifi. it sometimes detects them and sometimes not. Then when it asks for an encryption key, I assume it is asking for the password. Type in password, and nothing. No wifi connect. This is a toshiba netbook nb2401.

---

### Post by howefield on 2015-09-11
Right clicking the panel would likely have worked in as much as letting you add back the stuff you removed.

Start a new thread in [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") if you need help with the wifi issue.

---

### Post by CantankRus on 2015-09-11
To set the panel back to default, open a terminal and
kill the panel... 
```
killall lxpanel
```

delete your user config...
```
rm -rf ~/.config/lxpanel
```

Start lxpanel (nohup allows the application to continue running when the terminal is closed)...
```
nohup lxpanel &
```

---

### Post by Dennis N on 2015-09-11
You can use the command:

```
lxpanelctl restart
```

to reset the panel to its original state as installed.

---

### Post by CantankRus on 2015-09-11
> **Dennis N said:**
> You can use the command:

```
lxpanelctl restart
```

to reset the panel to its original state as installed.
Just reloads panel here.Doesn't reset to default.

---

