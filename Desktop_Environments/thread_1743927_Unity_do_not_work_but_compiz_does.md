---
title: "Unity do not work but compiz does"
date: 2011-04-29
forum: Desktop Environments
---

### Post by gufide on 2011-04-29
Hello there, I using a computer with a Nvidia geforce 4 and I use nouveau 3D, installed via jockey-gtk. Compiz work perfectly, but unity still don't work! This is my terminal output:
```
guillaume@Bureau:~$ unity --replace
unity-panel-service: aucun processus trouvé
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing debugspew options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing gnomecompat options...done
Initializing vpswitch options...done
Initializing move options...done
Initializing grid options...done
Initializing wall options...done
Initializing place options...done
Initializing scale options...done
Initializing resize options...done
Initializing animation options...done
Initializing expo options...done
Initializing unitymtgrabhandles options...done
Initializing session options...done
Initializing workarounds options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
compiz (unityshell) - Error: OpenGL 1.4+ not supported

compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Couldn't activate plugin 'unityshell'
Setting Update "detect_refresh_rate"
Setting Update "refresh_rate"
Setting Update "texture_filter"
Setting Update "lighting"
Setting Update "mipmap"
Setting Update "mouse_poll_interval"
Setting Update "run_command_terminal_key"
Setting Update "initiate_button"
Setting Update "top_left_corner_action"
Setting Update "top_right_corner_action"
Setting Update "left_edge_action"
Setting Update "right_edge_action"
Setting Update "bottom_left_corner_action"
Setting Update "arrow_base_color"
Setting Update "arrow_shadow_color"
Setting Update "no_slide_match"
Setting Update "edgeflip_move"
Setting Update "initiate_button"
Setting Update "mipmaps"
Setting Update "mipmap"

```Someone know what is the problem?

---

### Post by gufide on 2011-05-03
no one?

---

### Post by hornedfiend on 2011-05-06
I'm having the same issue on an antique hp compaq nx9105 laptop, with geforce4 mx440 64 vram.
Each time I select the "Ubuntu" session, the panels show up, but the unity launcher doesn't.
Additional drivers allowed me to install the experimental nvidia drivers and they show up as working, but I can't get unity to start, only classic desktop.

---

