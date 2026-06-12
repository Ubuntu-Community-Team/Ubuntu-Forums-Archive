---
title: "Gizmo problems"
date: 2006-06-07
forum: Desktop Environments
---

### Post by fastb on 2006-06-07
When I run Gizmo in terminal it says this:
```
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
gizmo: pcm.c:663: snd_pcm_close: Assertion `pcm' failed.
Aborted

```

---

### Post by nedkelly on 2006-07-27
I have the same problem!

EDIT:

From the forum post [URL="http://ubuntuforums.org/showthread.php?t=205924&page=2&highlight=dmix+plugin+supports+playback+stream"]http://ubuntuforums.org/showthread.php?t=205924&page=2&highlight=dmix+plugin+supports+playback+stream

[/URL]

I have got something there is working.

```
sudo mv /etc/asound.conf /etc/asound.conf.bak
sudo /etc/init.d/alsa-utils restart
```

Problem is I have followed the guide here [http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME]("http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME")

And I do not know what problems there can be in "removing" asound.conf

---

