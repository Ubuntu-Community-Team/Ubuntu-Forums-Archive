---
title: "xfce menu deleted. please help me restore it"
date: 2006-05-30
forum: Desktop Environments
---

### Post by yotama9 on 2006-05-30
hello

I have installed XFCE4 on my kubuntu machine last night and toyed around for a while

this morning I woke up t find there is no entries at my menu

when I click it I only get a tiny empty squre

the defoult menu is selceted and not my configure menu

any idea? 

thanks you all

---

### Post by yotama9 on 2006-05-30
no help?

it's driving me crazy this thing

no matter what I do it happen

other probelm I have is that after awhile of working the system jumps into extermly heavy load and I have no choice apart from hardware shutdown

please help me
please
thanks

---

### Post by deweese on 2006-05-31
I also had the menu disappear.  I only see wallpaper.  There are no icons on the desktop
and I only see the menu by right clicking.  It happened when I was trying to run
Easy Ubuntu.  The system crashed the first time and then it was like that.
The second try got easy ubuntu to work.

---

### Post by doobit on 2006-05-31
OK, here's a quick fix, but you'll need to do some work after to figure out what broke.
do ctrl+alt+backspace to drop back to the terminal. Then type startx and enter to get back to a login page. Change your default to Xfce and log in.

---

### Post by thewayofzen on 2006-06-01
Im going to guess thatyour menu is still totally fine.
The most common thing that happens to new xfce users with regards to the
menu is launching an app that replaces xfdesktop.  Most commonly this is
nautilus.  If u wish to run nautilus in xfce use  nautilus --no-desktop.

If you would like to have your menu back you only need to have your xfce configured to save settings on exit and then open a terminal and run

```
xfdesktop &
```

Logout out and log back in.
Im going to bet it fixes it.

---

### Post by wonko on 2006-06-01
I had the same problem and couldnt get any of the above working. I red this post: [http://www.ubuntuforums.org/showthread.php?t=184984]("http://www.ubuntuforums.org/showthread.php?t=184984")
and the reply by game_ender and finally it's working again. I had a little trouble copying the whole directory, though. Finally used this command: cp -R /etc/xdg/xfce4 ~/.config/
Maybe someone could make a howto for this? Seems many have this exact problem...

---

### Post by GarethMB on 2006-06-04
right click the Xfce menu

Properties

Use custom menu file and enter:

```
/etc/xdg/xfce4/desktop/menu.xml
```

---

### Post by dotnick on 2006-06-04
i was able to perform the following command, and after a few seconds i had full menu capabilities back in XFCE.  However, I still am not able to use the menu editor without it crashing with a segfault message.  I'm hoping that's an issue that will be resolved with the next set of updates.  I'm using Ubuntu with XFCE installed on top.  

```
$update-menus
```

---

### Post by braza on 2006-08-30
Hi! Maybe you can try run the following command within a terminal: 

$ xfce4-menueditor

Good luck!

---

### Post by trash on 2006-09-19
> **GarethMB said:**
> right click the Xfce menu

Properties

Use custom menu file and enter:

```
/etc/xdg/xfce4/desktop/menu.xml
```


I wonder why this file doesn't load when you select 'open default menu' in the menu editor... sure would solve a lot of problems.

---

