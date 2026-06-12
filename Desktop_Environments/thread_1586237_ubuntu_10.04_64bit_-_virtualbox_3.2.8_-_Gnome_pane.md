---
title: "ubuntu 10.04 64bit - virtualbox 3.2.8 - Gnome panel - mouse"
date: 2010-10-01
forum: Desktop Environments
---

### Post by hobbyhack on 2010-10-01
Last night I upgraded virtualbox from 3.1.8 to 3.2.8.  I am having an odd issue that started immediately after upgrading.  After I click anywhere in a full screen virtual box when I come back to the host I can no longer use my gnome panel (top bar).  If I click on Applications for example I can see that it has put a frame around the button, showing it was clicked, but the drop down menu never shows up.  If I click on a window in the host I can then use the gnome panel again.

My setup:

[LIST]
[*]Host: Pretty standard Ubuntu 10.04 64 bit install.  I typically only use the host to open up VBs, use a browser, and maybe gedit.  I also do some video editing on the host but not much is installed other than hardware packages beyond the base install.  Virtualbox 3.2.8 - installed from package provided by downlaod.virtualbox.org repositories.
[*]Hardware: 8gb of RAM, Nvidia graphics (compiz is working), Intel Core2Duo Quad, dedicated system and dedicated virtualbox hard drives using ext4 file systems (this is why I waited to install 3.2.x), logitech mx revolution mouse (btnx is installed), logitech g15 keyboard (with g15daemon and g15macro installed), 2 monitors (host on one, guest on the other in full screen)
[*]Guest OSes: Mostly debian squeeze servers but I also have a Ubuntu 10.04 guest for home stuff and a Windows XP guest for work
[*]Guest settings: New setting "Enable absolute pointing device" = disabled, USB is enabled but not in use
[/LIST]

Testing/Results:

[LIST]
[*]Upgraded guest additions to 3.2.8 - No change
[*]Uninstalled and resinstalled guest additions - No change
[*]Ubuntu and Windows guests have the same effect
[*]Window mode instead of full screen mode - Window mode works fine.  This only happens in full screen mode.
[*]Gnome panel still autohides and unhides
[*]Lower Gnome panel "bottom bar" is unaffected
[*]Tried with guest 3d and 2d disabled and enabled
[*]Once I use another window on the host I can then use the gnome panel again.  As soon as I click anywhere in guest problem is back.
[/LIST]

I am so excited about being able to have dual monitors in my guests I would really like to have 3.2.8 work.  I have posted this in the virtualbox forums also but I am not certain it is a virtualbox issue.  It is odd it only impacts Gnome Panel.

Any ideas or suggestions?

---

### Post by hobbyhack on 2010-10-05
I tried reinstalling Virtual Box with no luck.  I also noticed that this only impacts the drop down menus on the gnome panel.  The icons I have on panel work fine.

---

### Post by ask@refcapgroup.com on 2010-10-12
The problem it turns out has to do with the Mouse Integration with Virtualbox. You can get around this each time with a crude method. By simply pressing the host key. (Right Control). This will activate the gnome panel again.

---

### Post by hobbyhack on 2010-10-12
I tried upgrading to Virtualbox 3.2.10 today and the problem still exists.  I rolled back to virtuabox 3.1.8 and the problem went back away.

---

### Post by hobbyhack on 2010-10-12
There is a bug open now:
[http://www.virtualbox.org/ticket/7422](http://www.virtualbox.org/ticket/7422)

---

