---
title: "UNR- no gnome-panel or window manager"
date: 2009-04-24
forum: General Help
---

### Post by Seks on 2009-04-24
Hi, I installed netbook remix on my eee and set it in classic desktop mode, and those two things stopped starting when I log in. I uninstalled most of the NBR packages but it didn't make a difference.

I worked around it by adding gnome-panel and compiz to my startup apps, but it created a huge bottleneck. Deleting the gnome and gconf directories didn't solve anything like it seems to do for other people.

Does anyone know why it does this and how to fix it? There must be a systemwide configuration somewhere that's exclusive to the NBR version of jaunty. Setting compiz with system>prefs>appearence>visual effects doesn't work, it reverts to no window manager (but displays as "none") when I log out.

If no one knows how to fix this, can someone at least tell me how to make compiz and gnome-panel start a little earlier than the stuff in startup apps, so it doesn't load a windowmanager-less desktop and then dump compiz all over it?

---

### Post by Seks on 2009-04-25
Nevermind! I had never tried removing ~/.config, which was the source of the problem all along. Compiz and gnome-panel now start normally, no more slow login!

---

### Post by vector.kerr on 2009-05-05
I bought an eeePC 1000H netbook yesterday and I'm experiencing the same problem.

I've got a desktop but no gnome-wm (shortcut keys don't work) and no gnome-panel.

I got around the issue by creating a desktop shortcut to gnome-terminal and running gnome-wm & and gnome-panel &, but this is far from ideal.

I've been browsing and I came across [this bug](https://bugs.launchpad.net/netbook-remix-launcher/+bug/361625). This is a similar problem but I haven't removed UNR. I installed UNR from the moment I had the laptop, but I used the "Preferences > Switch Desktop Mode" tool to get my home-sweet-home desktop, as I prefer not having my app windows full-screened. After every log-off, I now lose gnome-panel and gnome-wm. I've created a shortcut to a quick shell app, in case anyone is having the same trouble and still looking for a workaround:

```
pkill gnome-wm
pkill gnome-panel
sleep 1
gnome-panel &
gnome-wm &
```

If anyone knows how to solve this issue that'd be awesome. Otherwise I'll just keep looking.

[edit]Looks like a possible solution might be to run the following in a terminal:
```
gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]
```
I'm guessing the "Switch Desktop Mode" application might not do this correctly, if this makes it work. I just logged off/on and my desktop re-appeared, so I'm going to reboot and see if it still does the trick.[/edit]

---

### Post by Farhadi on 2009-05-20
Its a bug in desktop-switcher described here:
[https://bugs.launchpad.net/desktop-switcher/+bug/349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)

you can fix this issue by installing this one:
[desktop-switcher_0.4.6_i386.deb]("http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb")

---

