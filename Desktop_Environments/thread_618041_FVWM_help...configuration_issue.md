---
title: "FVWM help...configuration issue"
date: 2007-11-20
forum: Desktop Environments
---

### Post by modestmelody on 2007-11-20
Currently, I'm using FVWM-crystal and I was editing one of my FvwmButtons panels, and unfortunately all of the icons are on top of each other rather than evenly spread across the bar.  Here is the relevant portion of the config
```

# Dock, applications panel and menu generator {{{1
All (ApplicationPanel) Close
DestroyModuleConfig ApplicationPanel: *
*ApplicationPanel: ActiveColorset $[cs-panel-active]
*ApplicationPanel: Colorset $[cs-panel-inactive]
*ApplicationPanel: Rows 1
*ApplicationPanel: Columns 5
*ApplicationPanel: Frame 0
*ApplicationPanel: (1x1, Icon /usr/share/pixmaps/firefox.png Action(Mouse 1) `Exec /opt/automatix/swiftweasel/swiftweasel`)
*ApplicationPanel: (1x2, Icon /usr/share/pixmaps/thunderbird.png Action(Mouse 1) `Exec /opt/automatix/swiftdove/swiftdove`)
*ApplicationPanel: (1x3, Icon /usr/share/pixmaps/pidgin-menu.xpm Action(Mouse 1) `Exec pidgin`)
*ApplicationPanel: (1x4, Icon /usr/share/pixmaps/vlc.png Action(Mouse 1) `Exec vlc`)
*ApplicationPanel: (1x5, Icon /usr/share/pixmaps/ktorrent.xpm Action(Mouse 1) `Exec ktorrent`)



# $[ApplicationPanelLength] is set by fvwm-crystal.apps, contains the number
# of the buttons on the panel
#PipeRead 'echo SetEnv FvwmButtons-Panel-Width $(($[ApplicationPanelLength]*40))'
#PipeRead 'echo *ApplicationPanel: Geometry 480x48-800+0

Module FvwmButtons -g 480x64-800+0 ApplicationPanel

```

What's wrong there?

---

