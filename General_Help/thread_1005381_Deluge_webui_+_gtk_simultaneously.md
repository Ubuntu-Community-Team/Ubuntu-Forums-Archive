---
title: "Deluge webui + gtk simultaneously?"
date: 2008-12-08
forum: General Help
---

### Post by Apocrathia on 2008-12-08
Okay so I've already asked this one over in the deluge forums and they weren't much help over there.
I like deluge a lot more than transmission on ubuntu for the simple fact that I can queue torrents. I use transmission on the mac as well and the queue function is there. I guess the programmers of Transmission were just drunk when they tried to port it to Linux. The webui of transmission is great because it'll automatically resize for the iphone and does the basic things you need it to, however the deluge webui is much more full featured.
so heres what I've been trying to do
```
deluged;deluge -u web;deluge -u gtk
```
I can get the webui up and running no problem, but when I try to start the gtk interface it craps out, and vice versa.
Here's what I get:
```

Traceback (most recent call last):
  File "/usr/bin/deluge", line 8, in <module>
    load_entry_point('deluge==1.0.5', 'console_scripts', 'deluge')()
  File "/var/lib/python-support/python2.5/deluge/main.py", line 99, in start_ui
    UI(options, args)
  File "/var/lib/python-support/python2.5/deluge/ui/ui.py", line 66, in __init__
    ui = WebUI(args)
  File "/var/lib/python-support/python2.5/deluge/ui/webui/webui.py", line 37, in __init__
    deluge_webserver.run(debug = False)
  File "/var/lib/python-support/python2.5/deluge/ui/webui/deluge_webserver.py", line 127, in run
    server.start()
  File "/var/lib/python-support/python2.5/deluge/ui/webui/lib/webpy022/wsgiserver/__init__.py", line 851, in start
    raise socket.error, msg
socket.error: (98, 'Address already in use')

```
I'm really not sure why I'm getting the error that a port is already in use, I've made damn sure the port is open for deluge. It makes no sense to me. If anyone here knows how to get the web interface to run on top of gtk, let me know. the reason I am trying to get this to work is (1) it does this in transmission with no problems. I guess the deluge programmers were drunk at this stage. The webui was so much better when it was just a plugin. & (2) The box everything runs off of is a headless server. I know it's odd to run x headless. I just suck at command line administration and I prefer just to vnc in if need be. So I'd still like the deluge gtk interface running in the background in case I need to get in to do something. Granted, most everything can be done from the deluge webui, but it just makes my head hurt a little less.
Anyone have any ideas?

---

