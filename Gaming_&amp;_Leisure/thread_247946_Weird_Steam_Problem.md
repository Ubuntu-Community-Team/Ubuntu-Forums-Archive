---
title: "Weird Steam Problem"
date: 2006-08-31
forum: Gaming &amp; Leisure
---

### Post by kob0724 on 2006-08-31
Allright, so I was having some issues before (the stuck at 26% thing), but I fixed that. Now I can get steam to run. It says steam updating but quickly goes to the account screen. As soon as that starts, i notice in the terminal all these errors pop up. I click on use existing account (cause I have one) and when I go to type in my account name no text shows up. Instead the letters show up in the terminal. I keep trying to type in the steam text box but I can't. So I exit out of it. Can anyone make sense of these errors?

When I start steam
```
fixme:process:IsWow64Process (0xffffffff 0x3b741c) stub!
fixme:shdocvw:ViewObject_SetAdvise (0xd820aa0)->(1 00000002 0x10216b0)
fixme:shdocvw:PersistStreamInit_InitNew (0xd820aa0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd820aa0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd820aa0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd820aa0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0xd821538)->(1 00000002 0x10216f0)
fixme:shdocvw:PersistStreamInit_InitNew (0xd821538)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd821538)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd821538)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd821538)->(ffffffff)

```

When I exit
```

err:systray:delete_icon invalid tray icon ID specified: 1d
Unable to remove c:\programfiles\steam\shortcuts.dat!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xd820aa0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xd820aa0)
fixme:shdocvw:OleObject_Close (0xd820aa0)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xd821538)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xd821538)
fixme:shdocvw:OleObject_Close (0xd821538)->(1)

``````

```

---

### Post by justin whitaker on 2006-08-31
Two questions:

Have you installed the mozcontrol activeX control and do you have all the fonts setup?

---

### Post by HAARP on 2006-08-31
Looks like the terminal gets keyboard focus.

Try starting steam with menu shortcut or something, but no terminal

---

### Post by kob0724 on 2006-08-31
I don't know what those two things are (mozcontrol and the other thing), so I'm going to assume I haven't.

How would I go about not starting it with the terminal?

---

### Post by tr4veler on 2006-09-01
> With latest Wine and Steam you should actually be able to type your login data into steam. If you can't type in your login, just right-click on the Login edit control in the Steam button and then left-click on it again to make the menu disappear. Voila! You can type your login now.

From [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games")

Worked for me.

---

### Post by HAARP on 2006-09-01
Press Alt+F2 and use this as a command line

---

