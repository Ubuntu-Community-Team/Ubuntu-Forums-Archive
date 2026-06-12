---
title: "[xubuntu] left click to show / hide windows in panel"
date: 2015-11-07
forum: Desktop Environments
---

### Post by rom117 on 2015-11-07
Hello,

I would like to show / hide windows from the panel. I am using xfce4-panel 4.11.0.
Currently, I do a **left click** to **maximize** a window and **middle click** to **minimize** it. How to do both actions on the same left click button? 

Thank you very much :).

Romain

---

### Post by vasa1 on 2015-11-07
> **rom117 said:**
> Hello,

I would like to show / hide windows from the panel. I am using xfce4-panel 4.11.0.
Currently, I do a **left click** to **maximize** a window and **middle click** to **minimize** it. How to do both actions on the same left click button? 

Thank you very much :).

RomainSo you want the left-click to work like a toggle when it's done in the specific context of clicking on an application's icon in the panel?

---

### Post by Dennis N on 2015-11-07
> How to do both actions on the same left click button? 

Probably not possible without using another key in addition. I suggest **right-click > minimize** and **right-click > unminimize**.

---

### Post by rom117 on 2015-11-07
> **vasa1 said:**
> So you want the left-click to work like a toggle when it's done in the specific context of clicking on an application's icon in the panel?

Yes exactly like a **toggle**. Not on the icons but on the windows titles (in the panel, the item is called "window buttons").
I had that functionality with the **lubuntu** panel and it was nice.

---

### Post by Dennis N on 2015-11-07
I retract my comment about it not being possible without another key. I checked my Xubuntu 15.10, and what you describe is exactly how it works on that version. Left-click acts as a toggle between minimized and unminimized. The panel is version 4.12.0-3ubuntu2.

I should check what my Xubuntu 14.04 does.

---

### Post by Dennis N on 2015-11-07
I checked an Xubuntu 14.04, and it behaves as I described in the previous post - left click is a toggle. Not surprising, since it has the same panel version 4.12.0. It was upgraded from the ppa you see in the display. 4.11 is the current version in the Ubuntu repository (via a mirror).

```
dmn@Kayleigh:~$ apt-cache policy xfce4-panel
xfce4-panel:
  Installed: 4.12.0-0ubuntu1~14.04
  Candidate: 4.12.0-0ubuntu1~14.04
  Version table:
 *** 4.12.0-0ubuntu1~14.04 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     4.11.0-0ubuntu1 0
        500 http://mirrors.xmission.com/ubuntu/ trusty/universe i386 Packages

```

Why not upgrade to 4.12, and it may solve your concerns.

---

### Post by rom117 on 2015-11-07
Just installed the latest version of the panel (xfce4-panel 4.12.0) following this link : [http://ubuntuportal.com/2015/03/how-to-upgrade-xfce-4-10-to-xfce-4-12-in-xubuntu-14-04-and-xubuntu-14-10.html](http://ubuntuportal.com/2015/03/how-to-upgrade-xfce-4-10-to-xfce-4-12-in-xubuntu-14-04-and-xubuntu-14-10.html)
After a reboot, it still does not work :(. What else could I do?

---

### Post by Dennis N on 2015-11-07
I just checked on a third machine that was not upgraded and still has the 4.11 xfce4-panel like yours, and the toggle with left-click works there too. So it is not likely the fault of the 4.11 panel version - something else is at fault on your system.

```
dmn@Sydney:~$ apt-cache policy xfce4-panel
xfce4-panel:
  Installed: 4.11.0-0ubuntu1
  Candidate: 4.11.0-0ubuntu1
  Version table:
 *** 4.11.0-0ubuntu1 0
        500 http://mirrors.us.kernel.org/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Upgrading to Xfce 4.12 may still be beneficial.

---

### Post by rom117 on 2015-11-07
Ok thanks for your search :).
Not sure it's useful but here is the output of the apt-cache policy command:
```
rom@rom-SATELLITE-C855-227:~$ apt-cache policy xfce4-panel
xfce4-panel:
  Installed: 4.12.0-0ubuntu1~14.04
  Candidate: 4.12.0-0ubuntu1~14.04
  Version table:
 *** 4.12.0-0ubuntu1~14.04 0
        500 [http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/](http://ppa.launchpad.net/xubuntu-dev/xfce-4.12/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     4.11.0-0ubuntu1 0
        500 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
```

---

### Post by Dennis N on 2015-11-07
> What else could I do?
Sorry - Didn't see your post #7 before I did post #8. Which way does your left-click work - to minimize, or to restore? If you click again to do the opposite, what happens - nothing?

---

### Post by rom117 on 2015-11-07
When I do a left click on a minimized window, it is displayed. If I do another left click on the displayed window, it does nothing :(. I think the title in the window is moving a bit to the bottom right / top left each time I do a left click on it.

---

### Post by Dennis N on 2015-11-07
That is very strange. Did you try a different mouse? Seems unlikely, but can't hurt to try. You may just have to use another method, like the right-click method on the window button using the context menu. And someone else may have some other ideas as to what is going on.

---

### Post by rom117 on 2015-11-07
Just found the solution :D. In the preferences of the Window Buttons items, set middle click action to nothing so the left click behaves like a toggle button (minimize / maximize). When the middle click action is set to minimize window, it inhibits the minimize window of the left click button!
Thanks for your help anyway, solved!

---

### Post by ajgreeny on 2015-11-07
The behaviour you want, ie toggle window, has always been the default behaviour of the xfce4 window-buttons in the panel as far as I'm aware, so there must be some setting that you have changed somewhere, or is not working as it should.

I have just tried this by setting the "middle click" to "minimise windows" in my Window-buttons preferences and with that setting toggle is disabled; change the Middle-click setting to "Nothing" and toggle action will return.

The forum software played tricks on me with a long delay when I was typing the above, which you have now found as the answer.  It also duplicated my post but I have now removed that.

---

### Post by Dennis N on 2015-11-07
> **rom117 said:**
> Just found the solution :D. In the preferences of the Window Buttons items, set middle click action to nothing so the left click behaves like a toggle button (minimize / maximize). When the middle click action is set to minimize window, it inhibits the minimize window of the left click button!
Thanks for your help anyway, solved!

Very interesting. I didn't know that about those preferences. Glad you discovered the reason. Sometimes if you just keep looking it pays off!

Edit: I see ajgreeny (a very knowledgeable fellow) has the reason nailed too.

---

