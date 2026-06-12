---
title: "want to add my own &quot;notification&quot; messages"
date: 2010-02-14
forum: Desktop Environments
---

### Post by SaintDanBert on 2010-02-14
I want to add my own "notification" pop-up messages to Ubuntu Karmic.
These appear as small black rectangles in the top right corner of the screen for all sorts of things that happen on my laptop: battery level, network connections, sound volume, screen brightness, etc.

I want to (1) understand where and how these existing notifications happen, and (2) be able to configure my own for whatever reason comes along.

Cheers,
~~~ 0;-Dan

---

### Post by zlatkart on 2010-02-14
Hope this works in Karmic the same way and you meant this:

 ```
notify-send -i terminal Text1 "Text2"
```

---

### Post by SaintDanBert on 2010-02-15
I don't find any **notify-send** anything on my Karmic installation.
When I search for packages
```

user@host $ dpkg -l | grep notify                        

ii  firefox-notify     1.5.4-1ubuntu1     integrate Firefox download messages with des
ii  inotify-tools                         3.13-1                                     command-line programs providing a simple int
ii  libinotifytools0                      3.13-1                                     utility wrapper around inotify
ii  libnotify1                            0.4.5-1ubuntu1                             sends desktop notifications to a notificatio
ii  notify-osd                            0.9.24-0ubuntu1                            daemon that displays passive pop-up notifica
ii  notify-osd-icons                      0.3                                        Notify-OSD icons
ii  python-notify                         0.1.1-2build2                              Python bindings for libnotify
ii  python-pyinotify                      0.8.6-2ubuntu2                             simple Linux inotify Python bindings
ii  python-pyinotify-doc                  0.8.6-2ubuntu2                             simple Linux inotify Python bindings -- docu
user@host $

```

Once I get THIS working, it will help some, but I also need to know how to tap in with whatever else the sub-system already does. Some of my notices modify what already happens.

Cheers,
~~~ 0;-Dan

---

### Post by freeball1 on 2010-02-15
You have to install libnotify-bin, it contains notify-send.

No idea, how to modify existing notifications, though.

---

