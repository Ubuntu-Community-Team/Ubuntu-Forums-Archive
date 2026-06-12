---
title: "Gnomebaker: plugin for wav files?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by quonsar on 2006-06-26
i just upgraded to dapper and installed gnomebaker with automatix. when i try to burn some wav files to an audio disk i get the message from gnomebaker: The plugin to handle a file of type audio/x-wav is not installed.

any clues what i need to do? :confused:

---

### Post by woedend on 2006-06-27
im guessing that it's because the gnomebaker you use depends on gstreamer .8, which isnt installed by default.  Try installing gstreamer0.8-plugins and see if that fixes it.

---

