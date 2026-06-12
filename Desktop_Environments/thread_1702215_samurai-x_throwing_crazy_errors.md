---
title: "samurai-x throwing crazy errors:"
date: 2011-03-07
forum: Desktop Environments
---

### Post by drnessie on 2011-03-07
I have tried to install the samurai-x window manager, because of its use of python. If no one can solve these errors, could someone please give me one that people seem to be **working on?**
```
[2011-03-07 19:02:20,904 INFO samuraix.main] logging everything to /tmp/sx.lastrun.log
[2011-03-07 19:02:20,905 INFO samuraix.main] trying to import config from /home/istom/.samuraix...
[2011-03-07 19:02:20,905 WARNING samuraix.main] /home/istom/.samuraix/config.py not found - using default config
[2011-03-07 19:02:20,927 INFO samuraix.appl] init
[2011-03-07 19:02:20,934 DEBUG samuraix.pluginsys] loading ['sxactions', 'sxdesktops', 'sxlayoutmgr', 'sxbind', 'yahiko_decorator', 'sxmoveresize', 'sxclientbuttons', 'sxfocus']
[2011-03-07 19:02:20,952 INFO samuraix.pluginsys] Loading plugin 'sxactions'...
[2011-03-07 19:02:20,957 INFO samuraix.pluginsys] Loading plugin 'sxdesktops'...
[2011-03-07 19:02:20,959 ERROR samuraix.pluginsys] The plugin 'sxlayoutmgr' couldn't be found!
[2011-03-07 19:02:20,959 ERROR samuraix.pluginsys] The plugin 'sxbind' couldn't be found!
[2011-03-07 19:02:20,960 INFO samuraix.pluginsys] Loading plugin 'yahiko_decorator'...
[2011-03-07 19:02:21,074 ERROR samuraix.pluginsys] The plugin 'sxmoveresize' couldn't be found!
[2011-03-07 19:02:21,074 ERROR samuraix.pluginsys] The plugin 'sxclientbuttons' couldn't be found!
[2011-03-07 19:02:21,074 ERROR samuraix.pluginsys] The plugin 'sxfocus' couldn't be found!
[2011-03-07 19:02:21,076 DEBUG samuraix.appl] found 1 screens
[2011-03-07 19:02:21,119 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27263033 (0x929186c)>
[2011-03-07 19:02:21,122 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92917cc>
[2011-03-07 19:02:21,123 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27263033 (0x929186c)> override_redirect is set
[2011-03-07 19:02:21,123 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=6291457 (0x929180c)>
[2011-03-07 19:02:21,124 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,124 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=6291457 (0x929180c)> - not viewable
[2011-03-07 19:02:21,124 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=10485761 (0x929164c)>
[2011-03-07 19:02:21,125 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92917cc>
[2011-03-07 19:02:21,125 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=10485761 (0x929164c)> - not viewable
[2011-03-07 19:02:21,126 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=12582913 (0x92917ac)>
[2011-03-07 19:02:21,126 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,126 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=12582913 (0x92917ac)> - not viewable
[2011-03-07 19:02:21,127 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=14680065 (0x929158c)>
[2011-03-07 19:02:21,127 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92917cc>
[2011-03-07 19:02:21,128 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=14680065 (0x929158c)> - not viewable
[2011-03-07 19:02:21,128 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=16777217 (0x929174c)>
[2011-03-07 19:02:21,129 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,129 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=16777217 (0x929174c)> - not viewable
[2011-03-07 19:02:21,129 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=14680067 (0x92915cc)>
[2011-03-07 19:02:21,130 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92917cc>
[2011-03-07 19:02:21,130 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=14680067 (0x92915cc)> - not viewable
[2011-03-07 19:02:21,130 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=18874369 (0x92916ec)>
[2011-03-07 19:02:21,131 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,131 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=18874369 (0x92916ec)> - not viewable
[2011-03-07 19:02:21,131 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=25165827 (0x929156c)>
[2011-03-07 19:02:21,132 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92917cc>
[2011-03-07 19:02:21,132 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=25165827 (0x929156c)> - not viewable
[2011-03-07 19:02:21,132 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27262977 (0x929168c)>
[2011-03-07 19:02:21,133 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,133 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27262977 (0x929168c)> - not viewable
[2011-03-07 19:02:21,134 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27262981 (0x929152c)>
[2011-03-07 19:02:21,134 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92917cc>
[2011-03-07 19:02:21,135 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27262981 (0x929152c)> - not viewable
[2011-03-07 19:02:21,135 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=18874371 (0x92915ec)>
[2011-03-07 19:02:21,135 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,137 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=18874371 (0x92915ec)> override_redirect is set
[2011-03-07 19:02:21,137 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=37748737 (0x92914ec)>
[2011-03-07 19:02:21,152 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92918ac>
[2011-03-07 19:02:21,152 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=37748737 (0x92914ec)> - not viewable
[2011-03-07 19:02:21,153 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=39845889 (0x92914cc)>
[2011-03-07 19:02:21,153 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,154 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=39845889 (0x92914cc)> - not viewable
[2011-03-07 19:02:21,154 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=41943041 (0x92913ec)>
[2011-03-07 19:02:21,154 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92918ac>
[2011-03-07 19:02:21,155 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=41943041 (0x92913ec)> - not viewable
[2011-03-07 19:02:21,155 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=44040193 (0x92913ac)>
[2011-03-07 19:02:21,155 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,156 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=44040193 (0x92913ac)> - not viewable
[2011-03-07 19:02:21,156 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=46137345 (0x929144c)>
[2011-03-07 19:02:21,157 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92918ac>
[2011-03-07 19:02:21,157 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=46137345 (0x929144c)> - not viewable
[2011-03-07 19:02:21,157 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27262987 (0x929148c)>
[2011-03-07 19:02:21,158 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,158 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27262987 (0x929148c)> - not viewable
[2011-03-07 19:02:21,158 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27262988 (0x92913cc)>
[2011-03-07 19:02:21,159 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92918ac>
[2011-03-07 19:02:21,159 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27262988 (0x92913cc)> - not viewable
[2011-03-07 19:02:21,159 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27262989 (0x92914ac)>
[2011-03-07 19:02:21,160 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,160 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27262989 (0x92914ac)> - not viewable
[2011-03-07 19:02:21,160 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27262990 (0x929134c)>
[2011-03-07 19:02:21,161 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92918ac>
[2011-03-07 19:02:21,161 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27262990 (0x929134c)> - not viewable
[2011-03-07 19:02:21,161 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27262996 (0x929142c)>
[2011-03-07 19:02:21,162 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,163 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27262996 (0x929142c)> override_redirect is set
[2011-03-07 19:02:21,163 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=27262997 (0x929132c)>
[2011-03-07 19:02:21,164 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92917cc>
[2011-03-07 19:02:21,164 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=27262997 (0x929132c)> - not viewable
[2011-03-07 19:02:21,165 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=41943043 (0x929130c)>
[2011-03-07 19:02:21,165 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,166 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=41943043 (0x929130c)> - not viewable
[2011-03-07 19:02:21,166 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=62914561 (0x929122c)>
[2011-03-07 19:02:21,167 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x92917cc>
[2011-03-07 19:02:21,167 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> not managing <Window XID=62914561 (0x929122c)> - not viewable
[2011-03-07 19:02:21,167 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x928b04c> found child <Window XID=28274409 (0x92911ec)>
[2011-03-07 19:02:21,183 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x928b1ac>
[2011-03-07 19:02:21,185 INFO samuraix.client] New client: Client=<Client at 0x9291dcc for <Window XID=28274409 (0x92911ec)>> Window=<Window XID=28274409 (0x92911ec)> Actor=<Window XID=28274409 (0x92911ec)>
[2011-03-07 19:02:21,187 WARNING samuraix.client] invalid size hints received: "'flags'"
[2011-03-07 19:02:21,187 DEBUG root] screen <samuraix.screen.Screen object at 0x928b04c> is now managing <Client at 0x9291dcc for <Window XID=28274409 (0x92911ec)>>
[2011-03-07 19:02:21,195 ERROR samuraix.main] Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/samurai_x2-0.2-py2.6.egg/samuraix/main.py", line 245, in run_app
    app.init()
  File "/usr/local/lib/python2.6/dist-packages/samurai_x2-0.2-py2.6.egg/samuraix/appl.py", line 141, in init
    screen.scan()
  File "/usr/local/lib/python2.6/dist-packages/samurai_x2-0.2-py2.6.egg/samuraix/screen.py", line 352, in scan
    self.manage(child)
  File "/usr/local/lib/python2.6/dist-packages/samurai_x2-0.2-py2.6.egg/samuraix/screen.py", line 241, in manage
    self.dispatch_event('on_new_client', self, client)
  File "/usr/local/lib/python2.6/dist-packages/ooxcb-1.1-py2.6.egg/ooxcb/eventsys.py", line 409, in dispatch_event
    if handler(*args):
  File "/usr/local/lib/python2.6/dist-packages/yahiko-0.1-py2.6.egg/yahiko/decorator.py", line 365, in on_new_client
    self.create_decoration(screen, client)
  File "/usr/local/lib/python2.6/dist-packages/yahiko-0.1-py2.6.egg/yahiko/decorator.py", line 373, in create_decoration
    decorator = Decorator(self, screen, client)
  File "/usr/local/lib/python2.6/dist-packages/yahiko-0.1-py2.6.egg/yahiko/decorator.py", line 147, in __init__
    self.create_actor_window()
  File "/usr/local/lib/python2.6/dist-packages/yahiko-0.1-py2.6.egg/yahiko/decorator.py", line 183, in create_actor_window
    xproto.EventMask.ButtonPress,
  File "/usr/local/lib/python2.6/dist-packages/ooxcb-1.1-py2.6.egg/ooxcb/protocol/xproto.py", line 4563, in create
    conn.core.create_window_checked(depth, win, parent, x, y, width, height, border_width, _class, visual, value_mask, value_list).check()
  File "/usr/local/lib/python2.6/dist-packages/ooxcb-1.1-py2.6.egg/ooxcb/cookie.py", line 69, in check
    Error.set(self.conn, error)
  File "/usr/local/lib/python2.6/dist-packages/ooxcb-1.1-py2.6.egg/ooxcb/protobj.py", line 154, in set
    raise exception(conn, inst)
BadMatch: (<ooxcb.conn.Connection object at 0x91f668c>, <ooxcb.protocol.xproto.MatchError object at 0x92919cc>)

istom@isToms-PC:~$ sx-wm
[2011-03-07 19:02:38,401 INFO samuraix.main] logging everything to /tmp/sx.lastrun.log
[2011-03-07 19:02:38,402 INFO samuraix.main] trying to import config from /home/istom/.samuraix...
[2011-03-07 19:02:38,402 WARNING samuraix.main] /home/istom/.samuraix/config.py not found - using default config
[2011-03-07 19:02:38,424 INFO samuraix.appl] init
[2011-03-07 19:02:38,430 DEBUG samuraix.pluginsys] loading ['sxactions', 'sxdesktops', 'sxlayoutmgr', 'sxbind', 'yahiko_decorator', 'sxmoveresize', 'sxclientbuttons', 'sxfocus']
[2011-03-07 19:02:38,448 INFO samuraix.pluginsys] Loading plugin 'sxactions'...
[2011-03-07 19:02:38,454 INFO samuraix.pluginsys] Loading plugin 'sxdesktops'...
[2011-03-07 19:02:38,457 ERROR samuraix.pluginsys] The plugin 'sxlayoutmgr' couldn't be found!
[2011-03-07 19:02:38,458 ERROR samuraix.pluginsys] The plugin 'sxbind' couldn't be found!
[2011-03-07 19:02:38,458 INFO samuraix.pluginsys] Loading plugin 'yahiko_decorator'...
[2011-03-07 19:02:38,567 ERROR samuraix.pluginsys] The plugin 'sxmoveresize' couldn't be found!
[2011-03-07 19:02:38,568 ERROR samuraix.pluginsys] The plugin 'sxclientbuttons' couldn't be found!
[2011-03-07 19:02:38,568 ERROR samuraix.pluginsys] The plugin 'sxfocus' couldn't be found!
[2011-03-07 19:02:38,570 DEBUG samuraix.appl] found 1 screens
[2011-03-07 19:02:38,618 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27263033 (0x865486c)>
[2011-03-07 19:02:38,618 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86547cc>
[2011-03-07 19:02:38,619 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27263033 (0x865486c)> override_redirect is set
[2011-03-07 19:02:38,620 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=6291457 (0x865480c)>
[2011-03-07 19:02:38,620 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,621 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=6291457 (0x865480c)> - not viewable
[2011-03-07 19:02:38,621 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=10485761 (0x865464c)>
[2011-03-07 19:02:38,621 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86547cc>
[2011-03-07 19:02:38,622 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=10485761 (0x865464c)> - not viewable
[2011-03-07 19:02:38,622 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=12582913 (0x86547ac)>
[2011-03-07 19:02:38,623 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,623 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=12582913 (0x86547ac)> - not viewable
[2011-03-07 19:02:38,623 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=14680065 (0x865458c)>
[2011-03-07 19:02:38,624 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86547cc>
[2011-03-07 19:02:38,624 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=14680065 (0x865458c)> - not viewable
[2011-03-07 19:02:38,625 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=16777217 (0x865474c)>
[2011-03-07 19:02:38,625 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,625 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=16777217 (0x865474c)> - not viewable
[2011-03-07 19:02:38,626 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=14680067 (0x86545cc)>
[2011-03-07 19:02:38,648 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86547cc>
[2011-03-07 19:02:38,648 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=14680067 (0x86545cc)> - not viewable
[2011-03-07 19:02:38,648 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=18874369 (0x86546ec)>
[2011-03-07 19:02:38,649 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,650 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=18874369 (0x86546ec)> - not viewable
[2011-03-07 19:02:38,650 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=25165827 (0x865456c)>
[2011-03-07 19:02:38,651 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86547cc>
[2011-03-07 19:02:38,651 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=25165827 (0x865456c)> - not viewable
[2011-03-07 19:02:38,651 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27262977 (0x865468c)>
[2011-03-07 19:02:38,652 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,652 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27262977 (0x865468c)> - not viewable
[2011-03-07 19:02:38,652 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27262981 (0x865452c)>
[2011-03-07 19:02:38,655 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86547cc>
[2011-03-07 19:02:38,655 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27262981 (0x865452c)> - not viewable
[2011-03-07 19:02:38,655 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=18874371 (0x86545ec)>
[2011-03-07 19:02:38,656 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,657 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=18874371 (0x86545ec)> override_redirect is set
[2011-03-07 19:02:38,658 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=37748737 (0x86544ec)>
[2011-03-07 19:02:38,658 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86548ac>
[2011-03-07 19:02:38,658 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=37748737 (0x86544ec)> - not viewable
[2011-03-07 19:02:38,659 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=39845889 (0x86544cc)>
[2011-03-07 19:02:38,673 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,673 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=39845889 (0x86544cc)> - not viewable
[2011-03-07 19:02:38,673 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=41943041 (0x86543ec)>
[2011-03-07 19:02:38,674 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86548ac>
[2011-03-07 19:02:38,674 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=41943041 (0x86543ec)> - not viewable
[2011-03-07 19:02:38,674 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=44040193 (0x86543ac)>
[2011-03-07 19:02:38,675 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,675 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=44040193 (0x86543ac)> - not viewable
[2011-03-07 19:02:38,675 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=46137345 (0x865444c)>
[2011-03-07 19:02:38,676 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86548ac>
[2011-03-07 19:02:38,676 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=46137345 (0x865444c)> - not viewable
[2011-03-07 19:02:38,677 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27262987 (0x865448c)>
[2011-03-07 19:02:38,677 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,677 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27262987 (0x865448c)> - not viewable
[2011-03-07 19:02:38,678 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27262988 (0x86543cc)>
[2011-03-07 19:02:38,678 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86548ac>
[2011-03-07 19:02:38,678 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27262988 (0x86543cc)> - not viewable
[2011-03-07 19:02:38,679 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27262989 (0x86544ac)>
[2011-03-07 19:02:38,679 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,680 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27262989 (0x86544ac)> - not viewable
[2011-03-07 19:02:38,680 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27262990 (0x865434c)>
[2011-03-07 19:02:38,680 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86548ac>
[2011-03-07 19:02:38,681 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27262990 (0x865434c)> - not viewable
[2011-03-07 19:02:38,681 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27262996 (0x865442c)>
[2011-03-07 19:02:38,681 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,682 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27262996 (0x865442c)> override_redirect is set
[2011-03-07 19:02:38,683 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=27262997 (0x865432c)>
[2011-03-07 19:02:38,683 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86547cc>
[2011-03-07 19:02:38,684 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=27262997 (0x865432c)> - not viewable
[2011-03-07 19:02:38,684 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=41943043 (0x865430c)>
[2011-03-07 19:02:38,685 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,685 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=41943043 (0x865430c)> - not viewable
[2011-03-07 19:02:38,685 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=62914561 (0x865422c)>
[2011-03-07 19:02:38,686 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86547cc>
[2011-03-07 19:02:38,686 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> not managing <Window XID=62914561 (0x865422c)> - not viewable
[2011-03-07 19:02:38,686 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=28275996 (0x86541ec)>
[2011-03-07 19:02:38,687 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x8654dcc>
[2011-03-07 19:02:38,690 INFO samuraix.client] New client: Client=<Client at 0x865c70c for <Window XID=28275996 (0x86541ec)>> Window=<Window XID=28275996 (0x86541ec)> Actor=<Window XID=28275996 (0x86541ec)>
[2011-03-07 19:02:38,706 WARNING samuraix.client] invalid size hints received: "'flags'"
[2011-03-07 19:02:38,707 DEBUG root] screen <samuraix.screen.Screen object at 0x864e04c> is now managing <Client at 0x865c70c for <Window XID=28275996 (0x86541ec)>>
[2011-03-07 19:02:38,709 DEBUG yahiko.decorator] created client actor client=<Client at 0x865c70c for <Window XID=28275996 (0x86541ec)>> actor=<Window XID=121634827 (0x8654dac)>
[2011-03-07 19:02:38,748 DEBUG samuraix.client] unbanning <Client at 0x865c70c for <Window XID=28275996 (0x86541ec)>>
[2011-03-07 19:02:38,757 DEBUG samuraix.screen] Screen. I am focusing <Client at 0x865c70c for <Window XID=28275996 (0x86541ec)>> <Window XID=28275996 (0x86541ec)> <Window XID=121634827 (0x8654dac)>
[2011-03-07 19:02:38,757 INFO samuraix.client] setting input focus on <Client at 0x865c70c for <Window XID=28275996 (0x86541ec)>>
[2011-03-07 19:02:38,809 DEBUG samuraix.screen] Screen. I am focusing <Client at 0x865c70c for <Window XID=28275996 (0x86541ec)>> <Window XID=28275996 (0x86541ec)> <Window XID=121634827 (0x8654dac)>
[2011-03-07 19:02:38,810 INFO samuraix.client] setting input focus on <Client at 0x865c70c for <Window XID=28275996 (0x86541ec)>>
[2011-03-07 19:02:38,810 DEBUG samuraix.screen] <samuraix.screen.Screen object at 0x864e04c> found child <Window XID=28274409 (0x865428c)>
[2011-03-07 19:02:38,812 DEBUG samuraix.screen] attr <ooxcb.protocol.xproto.GetWindowAttributesReply object at 0x86548ac>
[2011-03-07 19:02:38,814 INFO samuraix.client] New client: Client=<Client at 0x865ce4c for <Window XID=28274409 (0x865428c)>> Window=<Window XID=28274409 (0x865428c)> Actor=<Window XID=28274409 (0x865428c)>
[2011-03-07 19:02:38,816 WARNING samuraix.client] invalid size hints received: "'flags'"
[2011-03-07 19:02:38,816 DEBUG root] screen <samuraix.screen.Screen object at 0x864e04c> is now managing <Client at 0x865ce4c for <Window XID=28274409 (0x865428c)>>
[2011-03-07 19:02:38,824 ERROR samuraix.main] Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/samurai_x2-0.2-py2.6.egg/samuraix/main.py", line 245, in run_app
    app.init()
  File "/usr/local/lib/python2.6/dist-packages/samurai_x2-0.2-py2.6.egg/samuraix/appl.py", line 141, in init
    screen.scan()
  File "/usr/local/lib/python2.6/dist-packages/samurai_x2-0.2-py2.6.egg/samuraix/screen.py", line 352, in scan
    self.manage(child)
  File "/usr/local/lib/python2.6/dist-packages/samurai_x2-0.2-py2.6.egg/samuraix/screen.py", line 241, in manage
    self.dispatch_event('on_new_client', self, client)
  File "/usr/local/lib/python2.6/dist-packages/ooxcb-1.1-py2.6.egg/ooxcb/eventsys.py", line 409, in dispatch_event
    if handler(*args):
  File "/usr/local/lib/python2.6/dist-packages/yahiko-0.1-py2.6.egg/yahiko/decorator.py", line 365, in on_new_client
    self.create_decoration(screen, client)
  File "/usr/local/lib/python2.6/dist-packages/yahiko-0.1-py2.6.egg/yahiko/decorator.py", line 373, in create_decoration
    decorator = Decorator(self, screen, client)
  File "/usr/local/lib/python2.6/dist-packages/yahiko-0.1-py2.6.egg/yahiko/decorator.py", line 147, in __init__
    self.create_actor_window()
  File "/usr/local/lib/python2.6/dist-packages/yahiko-0.1-py2.6.egg/yahiko/decorator.py", line 183, in create_actor_window
    xproto.EventMask.ButtonPress,
  File "/usr/local/lib/python2.6/dist-packages/ooxcb-1.1-py2.6.egg/ooxcb/protocol/xproto.py", line 4563, in create
    conn.core.create_window_checked(depth, win, parent, x, y, width, height, border_width, _class, visual, value_mask, value_list).check()
  File "/usr/local/lib/python2.6/dist-packages/ooxcb-1.1-py2.6.egg/ooxcb/cookie.py", line 69, in check
    Error.set(self.conn, error)
  File "/usr/local/lib/python2.6/dist-packages/ooxcb-1.1-py2.6.egg/ooxcb/protobj.py", line 154, in set
    raise exception(conn, inst)
BadMatch: (<ooxcb.conn.Connection object at 0x85b968c>, <ooxcb.protocol.xproto.MatchError object at 0x865cfac>)
```

---

