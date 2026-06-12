---
title: "switch from netbook to classic desktop?"
date: 2010-05-01
forum: Desktop Environments
---

### Post by eltonw on 2010-05-01
Someone mentioned to me that in the LUCID beta you could change from the netbook (tabbed) interface to the classic desktop interface (drop-down menus). _I *have* searched the following link_:[http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide#gnome-do]("http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide#gnome-do")
... but I cannot find instructions on HOWTO do so.:confused:

LUCID LTS is now installed, but I cannot find any tools / options in the administration section.

[FONT="Comic Sans MS"][COLOR="Green"][SIZE="2"]Is there a way to switch the LUCID UNE from the netbook interface to the classic desktop?[/SIZE][/COLOR][/FONT]

---

### Post by nothingspecial on 2010-05-01
Search for any of these packages
```

go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```

in your menu - System > Preferences > Startup Applications

uncheck them

Then log out and back in again.

---

### Post by eltonw on 2010-05-02
> **nothingspecial said:**
> Search for any of these packages
```

go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
```

in your menu - System > Preferences > Startup Applications

uncheck them

Then log out and back in again.

**Of the above list, I find ONLY:** 
Maximus Window Management and Netbook Launcher, ***_in_*** the list of Startup Programs, and ***enabled***. 
I unchecked both, and rebooted. 
The other items are definitely ***not*** in the startup list. I've also tried a cold boot of the system, but no success.
I still get the tabbed netbook interface.  (After reboot, I verified and saw that both items were indeed UNchecked).

[FONT="Comic Sans MS"][COLOR="Sienna"]In Jaunty Jackalope (9.04) there was an applet to switch between netbook interface and classic desktop. This was disabled in Karmic Kola (9.10) because it was seriously buggy.[/COLOR] [/FONT]

... not doubting you, but have you tried the above procedure yourself? I don't seem to have any success.:confused:

---

### Post by nothingspecial on 2010-05-03
> **eltonw said:**
> [B]

... not doubting you, but have you tried the above procedure yourself? I don't seem to have any success.:confused:

Yeah, but that was a long time ago, in the first version the launched the netbook remix - intrepid maybe.

At the time, those were the packages that made the difference.

---

### Post by KMcC on 2010-05-03
I have the opposite problem: I upgraded my Karmic HP Mini 110 to Lucid and got neither netbook nor classic interface. The screen consisted of two rectangles: big brown on the bottom and header-width white along the top. No words or icons or images at all. By right-clicking on the top white I was able to add icons and from there to actually use the distribution. But it's definitely a home-brew situation.
 
Also, not having the netbook interface, I'm not getting the nice space-saving feature that I had before where the top bar of the applications' windows disappeared and were folded into the middle of the screen's top bar.

---

### Post by eltonw on 2010-05-06
> **nothingspecial said:**
> Yeah, but that was a long time ago, in the first version the launched the netbook remix - intrepid maybe.

At the time, those were the packages that made the difference.

I accidentally found out how to do so:

1) Go to Administration \ Login screen [unlock: your password is required]
2) When the computer starts up:
SELECT: Gnome
[Ubuntu Netbook Edition is the default]

after a reboot the classic desktop will appear.

---

### Post by KdotJ on 2010-05-06
Is there a way to set it up so you can choose between the normal desktop and UNR at the login screen?

---

### Post by eltonw on 2010-05-06
> **KdotJ said:**
> Is there a way to set it up so you can choose between the normal desktop and UNR at the login screen?
YES.
Once you configure it as mentioned in my post, at the next reboot/login _and thereafter_ you will have [COLOR="Teal"]_three options BEFORE getting to the desktop_[/COLOR]:
Language [default: english], Keyboard [US, etc] , and **Session** [UNE, Gnome, etc];)

---

### Post by KdotJ on 2010-05-06
lovely! thanks very much

---

### Post by acrocephalus on 2010-07-30
Hello!
I have tried the solution by eltonw but I keep getting the Netbook Edition desktop. Any idea?
Cheers!
Dani

---

### Post by eltonw on 2010-07-30
> **acrocephalus said:**
> Hello!
I have tried the solution by eltonw but I keep getting the Netbook Edition desktop. Any idea?
Cheers!
Dani

Once you logout and reboot, you should have a different screen which appears before you get into the desktop, [COLOR="Navy"]**and has dialogs along the bottom**[/COLOR]. One of them is [COLOR="DarkRed"]SESSIO[/COLOR]N from which you choose: KDE, Classic Desktop, GNOME. The latter is the one you want.

I regret that I cannot do a screen capture since this appears before you get into the selected desktop / session.

respectfully,

---

