---
title: "gnome-do rhythmbox plugin problem"
date: 2009-03-06
forum: General Help
---

### Post by jexdawg13 on 2009-03-06
i have installed gnome-do with the the correct repositories added to source.lst and my PPAs are all up to date

gnome-do works as well as every plugin except rhythmbox.

when i click the checkmark in gnome-do's preferences, i get
```
bert@beast:~$ gnome-do
Installing "Do.Rhythmbox,2.0" addin...
The following add-ins will be installed:
 - Rhythmbox v2.0
Installing Rhythmbox v2.0


ERROR: /home/bert/.local/share/gnome-do/plugins-0.8.0/addins/Do.Rhythmbox.2.0/Rhythmbox.dll already exists


```

i have deleted that rhythmbox.dll, reinstalled gnome-do and gnome-do-plugins all to no avail. i want rhythmbox to work - can anyone help me?

i'm running intrepid ibex. thanks

UPDATE:

i got it. i just deleted my whole .local/gnome-do/ folder and reinstalled. have a bunch of other errors now:```
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing

(Do:11921): Pango-CRITICAL **: pango_context_load_font: assertion `pango_font_description_get_family (desc) != NULL' failed

(Do:11921): Pango-CRITICAL **: pango_context_load_font: assertion `pango_font_description_get_family (desc) != NULL' failed
11991

(Do:11921): Pango-CRITICAL **: pango_context_load_font: assertion `pango_font_description_get_family (desc) != NULL' failed

(Do:11921): Pango-CRITICAL **: pango_context_load_font: assertion `pango_font_description_get_family (desc) != NULL' failed
11991

(Do:11921): Pango-CRITICAL **: pango_context_load_font: assertion `pango_font_description_get_family (desc) != NULL' failed

(Do:11921): Pango-CRITICAL **: pango_context_load_font: assertion `pango_font_description_get_family (desc) != NULL' failed
11991
11991
11991

```

but oh well, i'll get through it.

---

