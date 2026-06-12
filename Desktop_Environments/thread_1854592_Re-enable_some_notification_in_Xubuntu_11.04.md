---
title: "Re-enable some notification in Xubuntu 11.04"
date: 2011-10-04
forum: Desktop Environments
---

### Post by insecure hyena on 2011-10-04
Hi community, after a long search over the Internet I'm ending here asking something really trivial but toward I'm struggling to get a solution. The situation is that I've pressed the button "Never show again" on the notification related to the successful connection to a network and now I really don't know how to re-enable this damned notification. From the related GUI it seams that such an option is not present.
Please I need this notification!!!

---

### Post by insecure hyena on 2011-10-08
BUMP...C'mon community there must be somewhere a configuration file that can be edited to re-enable all the notification!
Now the problem is...Where did Xubuntu developer put this file?

---

### Post by relgames on 2012-05-15
Hi, I have the same question.
Anyone has a solution?..

---

### Post by neu5eeCh on 2012-05-15
> **relgames said:**
> Hi, I have the same question.
Anyone has a solution?..

It's not something I've tried to solve myself, but I think this is the direction I would go.

[xfconf-query]("http://docs.xfce.org/xfce/xfconf/xfconf-query")

For instance, see what you get when you type:

> xfconf-query -c xfce4-panel -l -v

**Edit:** I tried this on my own system and didn't find anything helpful. However, my thought is that the problem has to do with the settings for *xfce4-indicator-plugin.* I have to head off to work but, as a hail Mary, you might try doing a complete uninstall and re-install of the indicator-plugin -- the idea being that you would reset the preferences.

---

### Post by vasa1 on 2012-05-15
> **VTPoet said:**
> It's not something I've tried to solve myself, but I think this is the direction I would go.

[xfconf-query]("http://docs.xfce.org/xfce/xfconf/xfconf-query")
...

That's nice. Running "xfconf-query -l -v" as a starter gives:
```
Channels:
  xfce4-power-manager
  thunar-volman
  xfce4-settings-editor
  xsettings
  xfce4-mixer
  xfce4-appfinder
  xfce4-session
  xfce4-settings-manager
  pointers
  keyboards
  xfce4-panel
  xfwm4
  xfce4-desktop
  xfce4-notifyd
  xfce4-keyboard-shortcuts
  ristretto

```
in my case and then expanding to insert the specific channel like what you suggested gives more info:
```
xfconf-query -c xfce4-keyboard-shortcuts -l -v
```

Unfortunately, I couldn't see anything related to OP's problem even with "xfconf-query -c xfce4-notifyd -l -v"

---

### Post by vasa1 on 2012-05-15
> **VTPoet said:**
> ... However, my thought is that the problem has to do with the settings for *xfce4-indicator-plugin.* ...
I recently added Xfce 4.10 to Ubuntu 12.04 via [this ppa]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10") but I don't see this plug-in in my software list.

---

### Post by vasa1 on 2012-05-15
Anyway, let's hope something comes of [this]("http://askubuntu.com/questions/137295/xubuntu-12-04-how-to-enable-some-skipped-notifications").

---

### Post by relgames on 2012-05-16
> **vasa1 said:**
> Anyway, let's hope something comes of [this]("http://askubuntu.com/questions/137295/xubuntu-12-04-how-to-enable-some-skipped-notifications").
Yes they were able to answer my question :)
Just checked it - it worked

---

### Post by neu5eeCh on 2012-05-16
> **relgames said:**
> Yes they were able to answer my question :)
Just checked it - it worked

Hey, that's cool. At least I was in the right neighborhood. :wink:

---

### Post by neu5eeCh on 2012-05-16
As a side note: I've never liked the notification bubbles in XFCE. I like the blur and fade bubbles of Gnome. A while back, installing [udev-notifier]("http://www.omgubuntu.co.uk/2011/05/recieve-ubuntu-notifications-when-connecting-usb-peripherals-with-udev-notify/") had the added bonus of changing the XFCE notification bubbles to Gnome style bubbles. This worked in 11.04 and 11.10. Haven't tried it in 12.04.

---

