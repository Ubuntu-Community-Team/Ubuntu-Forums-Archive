---
title: "totem-xine cannot play embedded win32 codec videos"
date: 2005-12-04
forum: Desktop Environments
---

### Post by seltrus on 2005-12-04
Hi all,

I have an odd problem.  I can play restricted format videos with totem-xine without a problem if they are stored locally.  However, I cannot play the same videos when embedded in firefox.  I have the same problem when using the gxine plugin as well.

I have scoured the forums, google, etc. and haven't seen anyone with this problem.

For example, visiting home.att.net/~cherokee68/wmvtest2.html shows no video but the video works fine after downloading it from [http://home.att.net/~cherokee67/Budlight_sunburn.wmv](http://home.att.net/~cherokee67/Budlight_sunburn.wmv) .

Here is the commnand line output:
```

user@hostname:~$ firefox
NP_Initialize
totem_plugin_new_instance
Init scriptable instance
mode 1
argv[0] type application/x-mplayer2
argv[1] height 305
argv[2] width 320
argv[3] PARAM (null)
argv[4] fileName http://home.att.net/~cherokee67/Budlight_sunburn.wmv
argv[5] autostart 1
argv[6] ShowStatusBar 1
argv[7] volume 0
plugin_get_value 14
plugin_set_window
about to fork
Launching: /usr/lib/totem/totem-mozilla-viewer --xid 50335833 --width 320 --height 305 fd://0
waiting for signal org.totem_9180.MozillaPluginService
Received notification for :1.10
Received notification for :1.10
Received notification for org.totem_9180.MozillaPluginService
Received notification for org.totem_9180.MozillaPluginService
Done forking, new proxy=0x89965e0
leaving plugin_set_window
CMD line: /usr/lib/totem/totem-mozilla-viewer --xid 50335833 --width 320 --height 305 fd://0
plugin_set_window
existing window
resize
leaving plugin_set_window
** Message: totem_embedded_open 'fd://0'
plugin_get_value 15
** Message: unhandled variable 15
plugin_get_value 11
Returning that we support iface
plugin_get_value 268435466
Returning instance 0x89c0e40
** Message: GetHelperForLanguage
** Message: GetInterfaces
plugin_destroy
** Message: stop

```

I have also tried the instructions at [http://www.cs.cornell.edu/~djm/ubuntu/#setupgxine](http://www.cs.cornell.edu/~djm/ubuntu/#setupgxine) without any results.

Any ideas?

Thanks!

---

### Post by frodon on 2005-12-05
Install the media player connectivity extension of firefox, it will solve your issues i think. It did for me

---

