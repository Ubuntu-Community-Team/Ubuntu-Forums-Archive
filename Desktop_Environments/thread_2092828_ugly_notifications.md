---
title: "ugly notifications"
date: 2012-12-08
forum: Desktop Environments
---

### Post by petru.marginean on 2012-12-08
Hi,

The system notifications in my ubuntu are quite ugly.
(please see attached screenshot: black borders, gray background, big ugly fonts)

Another issues is they span across both monitors. 
(I've marked with a red line the common border for my monitors)
This is a problem since I usually keep the second monitor off to save energy.

I have ubuntu 12.10, lightdm, gnome-no effects.
I've tried to change the themes in gnome-tweak-tool but the notifications stay the same.

How can I change the notification schema?
Also how can I force the notifications to appear only on my primary monitor?

```
$> gnome-session --version
gnome-session 3.6.0

$> uname -a
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

```[IMG]https://dl.dropbox.com/u/65655385/notification.png[/IMG]

Please help,
PM

---

### Post by Frogs Hair on 2012-12-09
You may want to look at application at the link. I don't think it will help with the dual monitor issue though . With a single monitor the notification color is dependent on theme at least for my system. Make sure the app is 12.10 compatible at Launchpad.      [http://www.webupd8.org/2012/06/closable-movable-notifyosd.html](http://www.webupd8.org/2012/06/closable-movable-notifyosd.html)

---

### Post by petru.marginean on 2012-12-11
Hi,

Thanks for advise. Followed the instructions, but the ugly notifications are still there.
I've tried to change the background (to red, see below) but nothing changes.
Actually anything I change it has no effect whatsoever.

Also please notice the "no process found" message in the terminal:


[IMG]https://dl.dropbox.com/u/65655385/notification02.png[/IMG]

---

### Post by petru.marginean on 2012-12-11
I see the  notify-osd is not running, but I also cannot start it:

```
$> ps -ef | grep notify-osd

$> /usr/lib/notify-osd/notify-osd 
reading settings from '/home/user/.notify-osd'

** (notify-osd:4518): WARNING **: Another instance has already registered org.freedesktop.Notifications

** (notify-osd:4518): WARNING **: Could not register instance

```Please help,
PM

---

### Post by TheIronKnuckle on 2013-02-05
I'm also experiencing this problem.

I've also been getting this ugly bastard in the middle of the screen for contrast and volume for almost a year now and it's pissing me off:

[[IMG]http://s11.postimage.org/skzrhm8hr/Selection_002.jpg[/IMG]]("http://postimage.org/image/skzrhm8hr/")

10.04 had them working just fine! :P


I use gnome classic 2d no compiz standard etc etc etc whatever. The one  where the traditional setup is a bar both at the top and bottom of the  screen

Is there any fix known or forthcoming?

edit:

I've managed to make them a bit neater by removing notification-daemon package. This has pushed them all back into the corner where they belong. But they're still ugly buggers. Check this out: 
[[IMG]http://s17.postimage.org/r16ngatjf/Selection_002.jpg[/IMG]]("http://postimage.org/image/r16ngatjf/")
The colour seems to be off and the borders are solid black. very ugly. what I wanted is more like these shots from the notify-osd documentation on the wiki:
[IMG]https://wiki.ubuntu.com/NotifyOSD?action=AttachFile&do=get&target=notification-mouseout.png[/IMG][IMG]https://wiki.ubuntu.com/NotifyOSD?action=AttachFile&do=get&target=notification-mouseover.png[/IMG]

edit:
I can get back this behaviour by turning to compiz.
I do not want compiz. I want metacity.
Is there any way to get these working under gnome classic (No 3d effects)?

---

### Post by 3rdalbum on 2013-02-05
> **TheIronKnuckle said:**
> 
edit:
I can get back this behaviour by turning to compiz.
I do not want compiz. I want metacity.
Is there any way to get these working under gnome classic (No 3d effects)?

The transparency between notifications, and the semi-transparency in the notifications themselves, are 3D effects in themselves.

If you turn on compositing in Metacity (it's a gconf key, or a dconf key, from what I remember) you might get the transparency, but then that kinda defeats the "no effects" thing.

---

### Post by TheIronKnuckle on 2013-02-05
Thanks for the quick reply!

Yeah, I realised transparency isn't the issue/what I'm looking for. I just want the colours to be correct and the black box to bugger off. I've managed to get an only-just-working solution happening by using some notify-osd configuration system. I just made the inner bubble the same black as the outer box. Still not that pretty, but I can live with it. Only issue now is that the notification bubbles disappear way too fast (a second or less). Again. I can live with that, but it's kind of annoying

---

### Post by petru.marginean on 2013-03-03
The ugly notifications and notify-osd not running are still there.
Any idea how this can be fixed?

Thanks,
PM

---

### Post by black veils on 2013-03-06
have you tried replacing the notify osd or whichever ubuntu is using, with the xfce version? its called **xfce4-notifyd**. here is some info > The package name is xfce4-notifyd and it will only remove notify-osd (as they cannot co-exist) and the ubuntu-desktop metapackage. Latter one won't harm your system, but it has some downsides, see: [What are the downsides of removing ubuntu-desktop metapackage?]("http://askubuntu.com/questions/21497/what-are-the-downsides-of-removing-ubuntu-desktop-metapackage")
  ...trying it won't hurt your system, as you can always go back by re-installing the ubuntu-desktop metapackage.

 source [http://www.answeredubuntu.com/49796/replace_notifyosd_with_the_xfce_version](http://www.answeredubuntu.com/49796/replace_notifyosd_with_the_xfce_version)

there is also a tweak tool for it, you will find in **/usr/share/applications**. with root privileges of the file manager, you can right-click the **notifications** file, open in a text editor, then edit something about ***not show in... ***so it shows in the menu.

---

### Post by petru.marginean on 2013-03-21
Ok, found out:
- you first have to uninstall notification-daemon (use synaptic)
- then you kill the notification-daemon running processes
- make sure you have notify-osd installed (synaptic)

```
$> notify-send "hello"
```

More info here:
[http://askubuntu.com/questions/156521/how-to-set-notify-osd-as-default-in-gnome-classic-session](http://askubuntu.com/questions/156521/how-to-set-notify-osd-as-default-in-gnome-classic-session)

Regards,
PM

---

