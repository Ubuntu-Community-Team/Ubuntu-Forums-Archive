---
title: "Deluge Issue"
date: 2009-02-26
forum: General Help
---

### Post by rannday on 2009-02-26
):P

I recently ran into multiple issues with Ubuntu 8.10 due to my noobness to this OS (Basically, former Windows user, now slightly more educated). But I am still very new to Ubuntu, so a lot of things I haven't fully grasped yet.

So I ran into issues and decided to reformat again. Deluge was working perfect before. Now, every time I try to open it up, CRASH! ](*,) Nothing but a blank box with Deluge as the title and my system's looknfeel. Then it disappears. :cry:

I've surfed google for hours trying to find a solution, but nothing. [-X

[-o< Any insight would be appreciated. Transmission client just isn't cutting it, and I hate the overhead of others such as Vuze. 

Also, has anyone been having trouble trying to access the Ubuntu forums? I was finally able to after multiple tries, but typing ubuntuforums.org into the address bar kept giving very strange errors. :-?

Rann
\\:D/

---

### Post by taurus on 2009-02-26
Run deluge from a terminal and see what the error message is.

---

### Post by rannday on 2009-02-26
$ deluge
[ERROR   ] 16:16:13 config:271 Error writing new config file: [Errno 13] Permission denied: '/home/*/.config/deluge/ui.conf.new'
1.1.3
[ERROR   ] 16:16:16 config:271 Error writing new config file: [Errno 13] Permission denied: '/home/*/.config/deluge/gtkui.conf.new'
Traceback (most recent call last):
  File "/usr/bin/deluge", line 8, in <module>
    load_entry_point('deluge==1.1.3', 'console_scripts', 'deluge')()
  File "/var/lib/python-support/python2.5/deluge/main.py", line 120, in start_ui
    UI(options, args, options.args)
  File "/var/lib/python-support/python2.5/deluge/ui/ui.py", line 55, in __init__
    ui = GtkUI(args)
  File "/var/lib/python-support/python2.5/deluge/ui/gtkui/gtkui.py", line 200, in __init__
    self.filtertreeview = FilterTreeView()
  File "/var/lib/python-support/python2.5/deluge/ui/gtkui/filtertreeview.py", line 74, in __init__
    self.tracker_icons = TrackerIcons()
  File "/var/lib/python-support/python2.5/deluge/ui/tracker_icons.py", line 68, in __init__
    os.mkdir(self.image_dir)
OSError: [Errno 13] Permission denied: '/home/*/.config/deluge/icons'

I am going to reinstall and post again, not sure if this can be taken as pertinent info considering I can't remember if the last thing I've done with Deluge was remove, purge, remove from synaptic or what .. been a few days since I last messed with it and kinda gave up

---

### Post by taurus on 2009-02-26
> **rannday said:**
> $ deluge
[ERROR   ] 16:16:13 config:271 Error writing new config file: [Errno 13] Permission denied: '**/home/*/.config/deluge/ui.conf.new**'
1.1.3
[ERROR   ] 16:16:16 config:271 Error writing new config file: [Errno 13] Permission denied: '**/home/*/.config/deluge/gtkui.conf.new**'
Traceback (most recent call last):
  File "/usr/bin/deluge", line 8, in <module>
    load_entry_point('deluge==1.1.3', 'console_scripts', 'deluge')()
  File "/var/lib/python-support/python2.5/deluge/main.py", line 120, in start_ui
    UI(options, args, options.args)
  File "/var/lib/python-support/python2.5/deluge/ui/ui.py", line 55, in __init__
    ui = GtkUI(args)
  File "/var/lib/python-support/python2.5/deluge/ui/gtkui/gtkui.py", line 200, in __init__
    self.filtertreeview = FilterTreeView()
  File "/var/lib/python-support/python2.5/deluge/ui/gtkui/filtertreeview.py", line 74, in __init__
    self.tracker_icons = TrackerIcons()
  File "/var/lib/python-support/python2.5/deluge/ui/tracker_icons.py", line 68, in __init__
    os.mkdir(self.image_dir)
OSError: [Errno 13] Permission denied: '/home/*/.config/deluge/icons'

I am going to reinstall and post again, not sure if this can be taken as pertinent info considering I can't remember if the last thing I've done with Deluge was remove, purge, remove from synaptic or what .. been a few days since I last messed with it and kinda gave up

Is your login name really *?

---

### Post by binbash on 2009-02-26
own  /home/YOURUSERNAME/.config/deluge folder with chown command (dont forget to change your username) or you can chmod 777 -R /home/YOURUSERNAME/.config/deluge but i don't suggest that

---

### Post by rannday on 2009-02-27
no, it is not *

I'll give that a try and get back to you

What would be the actual command?

tried

```
chown /home/myUserName/.config/deluge
```

got

chown: missing operand after `/home/myUserName/.config/deluge'

then searched

chown --help

but couldn't find anything that made sense to me, not familiar with chown


btw, if you haven't heard about the latest developments in California, check it out! GREAT NEWS! \\:D/

[http://www.cnn.com/video/#/video/bestoftv/2009/02/24/wian.pot.tax.cnn](http://www.cnn.com/video/#/video/bestoftv/2009/02/24/wian.pot.tax.cnn)
[http://www.ktvu.com/news/18777218/detail.html#-](http://www.ktvu.com/news/18777218/detail.html#-)

---

### Post by 944jon on 2009-02-28
Try this : 
rm ~/.config/deluge/persistent.state

Dunno what it exactly does, but found it on another thread, and worked for me.
I'm running 8.10, and Deluge 0.5.9.3

I had to add all my torrents over again though, and it loses them when I restart deluge.

---

