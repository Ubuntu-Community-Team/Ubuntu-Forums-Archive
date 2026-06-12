---
title: "Is there something like xfce4-panel-compiz for Ubuntu?"
date: 2017-05-13
forum: Desktop Environments
---

### Post by Pablo_San_Martn on 2017-05-13
Installed compiz a couple of days ago and came across this in the ArchWiki: [https://aur.archlinux.org/packages/xfce4-panel-compiz/](https://aur.archlinux.org/packages/xfce4-panel-compiz/)

Is there a similar package for Xubuntu? I'm using 16.04.

---

### Post by vasa1 on 2017-05-13
There doesn't seem to be anything like that in the standard repositories. 
```
apt search compiz | grep -i xfce
```comes up empty.

You may need to look at Launchpad in case someone has a ppa.

---

### Post by Pablo_San_Martn on 2017-05-13
> **vasa1 said:**
> You may need to look at Launchpad in case someone has a ppa.

Thanks vasa1, prompt as always.

I took a look and there seems to be an older patch for the issue I'm facing: [https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1292820](https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1292820)

I don't know how to install it, though.

---

### Post by vasa1 on 2017-05-13
I don't know. I'm assuming you'll need to edit source code, compile, etc. And here's what some people at the Xfce forum think: [https://forum.xfce.org/viewtopic.php?id=10739](https://forum.xfce.org/viewtopic.php?id=10739)

---

### Post by Pablo_San_Martn on 2017-05-13
Thanks again! Yeah, I agree it sounds like a contradiction. Personally, I don't like to have fancy DEs like Unity or Plasma on my work machine, but I have the resources and find some basic desktop animations really useful (e.g. wall while changing workspace to remember where I am). Using Xfce + compiz is perhaps like eating something between a plain salad and a double cheeseburger.

---

### Post by Pablo_San_Martn on 2017-05-13
Just realised that compiz is technically dead now that Unity was dropped. My bad.

---

### Post by monkeybrain20122 on 2017-05-14
> **Pablo_San_Martn said:**
> Just realised that compiz is technically dead now that Unity was dropped. My bad.

Actually that is not true. There is a compiz 0.8 [fork]("https://github.com/compiz-reloaded"). There are some recent videos posted on Youtube. It is incompatible with unity's 0.9 branch but since you are using xfce it doesn't matter. If you are on 16.04 you can install it via a [ppa]("https://launchpad.net/~adamsmith/+archive/ubuntu/compiz-reloaded").

---

### Post by flocculant on 2017-05-15
> wall while changing workspace to remember where I am
You can do that without compiz.

---

### Post by Pablo_San_Martn on 2017-05-18
> **monkeybrain20122 said:**
> Actually that is not true. There is a compiz 0.8 [fork]("https://github.com/compiz-reloaded"). There are some recent videos posted on Youtube. It is incompatible with unity's 0.9 branch but since you are using xfce it doesn't matter. If you are on 16.04 you can install it via a [ppa]("https://launchpad.net/~adamsmith/+archive/ubuntu/compiz-reloaded").

Cheers, that's great news!

---

### Post by Pablo_San_Martn on 2017-05-18
> **flocculant said:**
> You can do that without compiz.

What compositor would you recommend for the wall effect? 

I don't think xfwm4 or compton can do that? I only know about kwin, which is as heavy as compiz, plus all the qt libraries you need to install in Xfce.

---

### Post by again? on 2017-05-18
If the only reason you use compiz is for a desk switching indication,
I have a python script you can autostart in xfce which will display a notification when you switch workspaces.
Not mine. Picked up somewhere along the way.
_desk-notify.py_
```
#!/usr/bin/env python3

import gi
gi.require_version('Wnck', '3.0')
gi.require_version('Notify', '0.7')
from gi.repository import Wnck, Gtk, Notify
import signal, time

class Kludge:
    def __init__(self):
        self.first = True
        signal.signal(signal.SIGINT, signal.SIG_DFL)
        self.screen = Wnck.Screen.get_default()
        Notify.init("Workspace Switch Notifier")

    def fire_the_kludge(self, data_a, data_b):
        time.sleep(.1)
        try:
            workspace_num = str(self.screen.get_active_workspace().get_number() +1)
        except:
            workspace_num = "Some error happened"
        popup = Notify.Notification.new("DESK:  " + workspace_num)
        popup.show()
        time.sleep(2)
        popup.close()

    def main(self):
        self.screen.connect("active-workspace-changed", self.fire_the_kludge)
        Gtk.main()

if __name__ == '__main__':
    print("Here comes the kludge")
    kludge = Kludge()
    kludge.main()
```

---

### Post by vasa1 on 2017-05-18
> **guber2 said:**
> ...
Not mine. Picked up somewhere along the way.
...
Something very close is here: [https://unix.stackexchange.com/a/144307/](https://unix.stackexchange.com/a/144307/) with a link to [https://github.com/aking1012/chromiumKludge/blob/master/kludge.py](https://github.com/aking1012/chromiumKludge/blob/master/kludge.py)

---

### Post by Pablo_San_Martn on 2017-05-19
> **guber2 said:**
> _desk-notify.py_

Thanks [**[COLOR=#000000]guber2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2063040")! Should I make that file executable and add it to Application Autostart?

---

### Post by again? on 2017-05-19
> **Pablo_San_Martn said:**
> Thanks [**[COLOR=#000000]guber2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2063040")! Should I make that file executable and add it to Application Autostart?
Yessireee.
Test it works first by running in terminal and switching desktops.

---

