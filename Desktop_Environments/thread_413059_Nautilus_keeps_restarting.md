---
title: "Nautilus keeps restarting"
date: 2007-04-18
forum: Desktop Environments
---

### Post by billybag on 2007-04-18
For some reason mu Nautilus won't stay open. When i first login, my desktop appears fine (icons are there) but then my icons dissapear and my nautilus opens (with my home folder) and then closes. It does this over and over and then just stops and nautilus doesnt work.

please help

i tried reistalling nautilus already and that didnt work.

---

### Post by billybag on 2007-04-18
If this helps:

```

root@Waffle:/home/billy # nautilus

(nautilus:6941): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension
totem-video-thumbnailer couln't open file 'file:///home/billy/Desktop/000c7b0k'
Reason: Video codec 'WVC1' is not handled. You might need to install additional plugins to be able to play some types of movies.
Error: Document has not the mandatory ending %EOF
totem-video-thumbnailer couln't open file 'file:///home/billy/Desktop/main.swf'
Reason: There is no plugin to handle this movie..
SWFDEC: ERROR: swf.c(669): swfdec_decoder_experimental: using experimental code
SWFDEC: ERROR: actions.c(232): action_script_call: action script error (see warnings)
SWFDEC: ERROR: actions.c(232): action_script_call: action script error (see warnings)
SWFDEC: ERROR: actions.c(232): action_script_call: action script error (see warnings)
SWFDEC: ERROR: actions.c(232): action_script_call: action script error (see warnings)
SWFDEC: ERROR: actions.c(232): action_script_call: action script error (see warnings)
SWFDEC: ERROR: swfdec_bits.c(120): swfdec_bits_get_u16: reading past end of buffer

** ERROR **: file swfdec_bits.c: line 120 (swfdec_bits_get_u16): should not be reached
aborting...
Aborted (core dumped)

```

---

### Post by billybag on 2007-04-18
Oklie doklie. I removed those two files that were causing errors and now things sem to be fine. YAY. Anyone know why this happened though?

---

