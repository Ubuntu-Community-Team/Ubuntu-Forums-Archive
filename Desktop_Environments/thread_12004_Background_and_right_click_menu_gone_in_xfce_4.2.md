---
title: "Background and right click menu gone in xfce 4.2"
date: 2005-01-21
forum: Desktop Environments
---

### Post by Valavien on 2005-01-21
HI all,

This is the second time this has happened and I reinstalled the first time as I thought it was something I had done but it has done it again and I don't think I did anything!

While in XFCE my background dissapears and it turns into the default Ubuntu background and when I right click to access the xfce menu I get what you would get while using gnome!

Any ideas?
Maybe I should just stick with gnome/metacity.

---

### Post by Valavien on 2005-01-21
I now know the problem I just need to fix it.  Nautilus is loading and over riding xfdesktop.  I just need to work out how to run that and then save the settings.

Type "xfdesktop &" in a terminal and then save the session

more info:
[http://forum.xfce.org/viewtopic.php?t=1448](http://forum.xfce.org/viewtopic.php?t=1448)

---

### Post by dejitarob on 2005-02-04
Solution was posted on that thread:
> The session manager doesn't seem to remember command line arguments passed to the programs that you save. So it will only remember you were running "nautilus" and run that for the next session.

You can work around this by setting nautilus to always open in browser windows (in edit->preferences) and then configuring it via gconf to *not* draw the desktop. [uncheck](apps->nautilus->preferences->show_desktop)

---

### Post by dejitarob on 2005-02-05
Mine still does it occasionally with the above remedies. Draw_background under desktop -> gnome -> background might need to be unchecked as well.

---

### Post by dejitarob on 2005-02-06
Hmm my desktop is still reverting back to nautilus/gnome upon login. If I run 'xfdesktop &' in a terminal it works but the terminal spams 'attempt to put segment in horiz list twice' and if I close the terminal, desktop reverts back.

---

### Post by wulf on 2005-04-26
I've just upgraded from Warty to Hoary and hit the same problem - *xfdesktop &* seems to have sorted it out for the moment, so that's a big sigh of relief from me! Let's float this back to the top in case anyone else has hit the same issue (it took a bit of persistence in searching to dig up the answer).

Wulf

---

### Post by Psquared on 2005-05-27
Same problem here.

"xfdesktop &" fixes the background, but not the right click menu. Changing Nautilus settings does not help either.

---

### Post by ~art on 2006-08-16
No right click and empty menu's.

This is a pain.
I unstalled xfce completely which I thought would remove config files. However on reinstalling my old config has returned, cos my menu edits are there.no right click.

The full uninstall is not doing what it should - delete the config files.


I did another full uninstall and manually deleted the cache files and anything xfce related in my home folder then reinstalled.

Now I have my right click back. Added the xfce menu so if I lose the right click again I can still find applications.

When I changed resolution or perhaps the sessions and startup sessions screen I lost my right click again. The desktop setting 'allow xfce to manage the desktop' had been deselected one of these config utilities. Reselecting it returned my right click.

So until it happens again I am happy. By the way I'm on dapper 6.06.
This is a serious problem because I was left with no way to do anything (for a linux noob), cos I had no menu. I managed to add the xfce menu to the top bar but it was empty or did nothing. I didn't even have a terminal. All I could do was add items to the program launcher which isn't easy if you dont know where the are.
Luckily I could do a cnt alt backspace to get back to gnome and had another computer to access the internet on. Also I was being thrown into 640x480 resolution and it wouldn't let me change it.

That's another 6 hours wasted.:mad: 

Trying to switch to linux has been a real pain. Gnome is too slow on my computer, KDE kept crashing, and xfce was great until this happened. There is a long way to go before I'll be recommending that my mother switch to linux. That will be the acid test of usability.

---

### Post by dolby on 2006-08-17
when some things happen , for some reason xfce is not allowed to manage the desktop.

---

### Post by siacs on 2006-08-18
~art, most of the time when I see someone with this problem, it's because they've run Nautilus, which takes over the desktop. Running Xfdesktop will give control back to XFCE and bring back the right click menu. Remember if you want to run Nautilus to use the command nautilus --no-desktop.

Empty menus can occur if the menu is edited incorrectly or using a bad graphical menu editor. Here's a useful link on menu editing.

[http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu](http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu)

---

### Post by fragmented_user on 2006-08-20
Hi.

I have good news for you or anyone else plauged with these problems. Just complete these 2 easy steps.

1.Please run "strace xfdesktop" from the command line, wait until xfdesktop crashes (screen goes black again), save the output as a text file, and post it here.

2.Click this [link]("https://launchpad.net/distros/ubuntu/+source/xfwm4/+bug/57006") or visit [https://launchpad.net/distros/ubuntu/+source/xfwm4/+bug/57006](https://launchpad.net/distros/ubuntu/+source/xfwm4/+bug/57006) and follow the instructions on that page.

-Joseph

---

### Post by fortran01 on 2006-09-12
If all of the above remedies do NOT work. Try killing **xffm-deskview**.

You can see the PID (process id) of xffm-deskview using the command ```
ps aux | grep deskview
```

To kill:

```
kill <pid here>
```

Then start **xfdesktop** using ```
xfdesktop &
```

---

