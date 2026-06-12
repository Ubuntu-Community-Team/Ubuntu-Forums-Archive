---
title: "Firefox crashing"
date: 2005-11-28
forum: Desktop Environments
---

### Post by nix4me on 2005-11-28
Is there ever going to be a Firefox that doesn't crash all the time?

I thought it was 1.07 so I installed 1.5 rc3.  Still crashes.
I thought it was mplayer plugin 3.05 so I installed 3.11.  Still crashes.
I thought it was user agent extension.  Uninstalled that and still crashes.

Granted it doesn't crash all the time, but usually when hitting the back button.

Any ideas out there?

nix4me

---

### Post by 23meg on 2005-11-28
Run it from the terminal and see if it outputs any error messages during the crash there.

---

### Post by arazaxirelcinellersadolur on 2005-11-29
i have too the same firefox crashing/closing by itself ramdomly.
i do not want that firefox will play mpeg or wav etc. by itself on its window but i want to install it to harddisk and play it by totem.
i remove plug-in through preferences.
and i post to you my terminal messages abotu firefox:

1.elcin@memmedzadee:~$ firefox
NP_Initialize
totem_plugin_new_instance
Init scriptable instance
mode 1
argv[0] type application/x-mplayer2
argv[1] pluginspage [http://www.microsoft.com/Windows/Downloads/Contents/Products](http://www.microsoft.com/Windows/Downloads/Contents/Products) /MediaPlayer/
argv[2] filename /scripts/klip/klips/gsfb1.wmv
plugin_get_value 14
plugin_set_window
about to fork
Launching: /usr/lib/totem/totem-mozilla-viewer --xid 42122450 fd://0
waiting for signal org.totem_11143.MozillaPluginService
Received notification for :1.3
Received notification for :1.3
Received notification for org.totem_11143.MozillaPluginService
Received notification for org.totem_11143.MozillaPluginService
Done forking, new proxy=0x8a3c498
leaving plugin_set_window
plugin_set_window
existing window
resize
leaving plugin_set_window
plugin_set_window
existing window
resize
leaving plugin_set_window
CMD line: /usr/lib/totem/totem-mozilla-viewer --xid 42122450 fd://0
** Message: totem_embedded_open 'fd://0'
plugin_get_value 15
** Message: unhandled variable 15
plugin_get_value 11
Returning that we support iface
plugin_get_value 268435466
Returning instance 0x8319240
** Message: GetHelperForLanguage
** Message: GetInterfaces
plugin_destroy
** Message: stop
Die scriptable instance
NP_Initialize
totem_plugin_new_instance
Init scriptable instance
mode 1
argv[0] type application/x-mplayer2
argv[1] pluginspage [http://www.microsoft.com/Windows/Downloads/Contents/Products](http://www.microsoft.com/Windows/Downloads/Contents/Products) /MediaPlayer/
argv[2] filename /scripts/klip/klips/gsfb1.wmv
plugin_get_value 14
plugin_set_window
about to fork
Launching: /usr/lib/totem/totem-mozilla-viewer --xid 42125613 fd://0
waiting for signal org.totem_11173.MozillaPluginService
Received notification for :1.4
Received notification for :1.4
Received notification for org.totem_11173.MozillaPluginService
Received notification for org.totem_11173.MozillaPluginService
Done forking, new proxy=0x90a4ee8
leaving plugin_set_window
plugin_set_window
existing window
resize
leaving plugin_set_window
plugin_set_window
existing window
resize
leaving plugin_set_window
CMD line: /usr/lib/totem/totem-mozilla-viewer --xid 42125613 fd://0
** Message: totem_embedded_open 'fd://0'
plugin_get_value 15
** Message: unhandled variable 15
plugin_get_value 11
Returning that we support iface
plugin_get_value 268435466
Returning instance 0x8837638
** Message: GetHelperForLanguage
** Message: GetInterfaces
plugin_destroy
** Message: stop
Die scriptable instance
elcin@memmedzadee:~$


2.elcin@memmedzadee:~$ firefox
NP_Initialize
totem_plugin_new_instance
Init scriptable instance
mode 2
argv[0] type video/mpeg
argv[1] src [http://www.nubiles.net/samples/laura/nubiles_laura_sample.mpg](http://www.nubiles.net/samples/laura/nubiles_laura_sample.mpg)
argv[2] name plugin
argv[3] height 100%
argv[4] width 100%
plugin_get_value 14
plugin_set_window
about to fork
Launching: /usr/lib/totem/totem-mozilla-viewer --xid 41951838 --width 100 --height 100 --url [http://www.nubiles.net/samples/laura/nubiles_laura_sample.mpg](http://www.nubiles.net/samples/laura/nubiles_laura_sample.mpg) fd://0
waiting for signal org.totem_15182.MozillaPluginService
Received notification for :1.13
Received notification for :1.13
Received notification for org.totem_15182.MozillaPluginService
Received notification for org.totem_15182.MozillaPluginService
Done forking, new proxy=0x8a577e8
leaving plugin_set_window
plugin_set_window
existing window
resize
leaving plugin_set_window
plugin_set_window
existing window
resize
leaving plugin_set_window
plugin_new_stream
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
CMD line: /usr/lib/totem/totem-mozilla-viewer --xid 41951838 --width 100 --height 100 --url [http://www.nubiles.net/samples/laura/nubiles_laura_sample.mpg](http://www.nubiles.net/samples/laura/nubiles_laura_sample.mpg) fd://0
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
plugin_write_ready
plugin_write
** Message: ret -1
plugin_destroy_stream
** Message: totem_embedded_open 'fd://0'
** Message: error: There were no decoders found to handle the stream, you might need to install the corresponding plugins
plugin_destroy
** Message: stop
Die scriptable instance
Segmentation fault
elcin@memmedzadee:~$


So, i reinstalled firefox using sinaptic and again removed the plug-ins that have been clicked at preferences.
my totem is playing mpegs or wavs i installed the totem multimedia plugins.

best regards.

---

