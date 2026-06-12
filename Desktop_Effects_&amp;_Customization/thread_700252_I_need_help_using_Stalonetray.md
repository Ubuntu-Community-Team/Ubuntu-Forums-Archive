---
title: "I need help using Stalonetray"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by Bob Morane on 2008-02-18
Hello, i recently discovered this Stand Alone Tray as a replacement for the (often rather ugly) gnome panel notification area. It's suggested to be used with AWN as the AWN notification applet is ugly and unstable. However, there is not that much documentation on it (well, nearly nothing).

I have read the manual pages, and should have a .stalonetrayrc file in my home, but i don't. Do i have to create it by hand. Also, if i have such a file, do i just have to add some command line options inside to have them used by the tray when it's started.

When i launch it, i have a solid grey background. Well, i guess i just have to use -t option but i don't know how to get other nice effects. What's the effect of tinting for instance
––tint–color, tint_color [bool]
    Set tinting color. Default value: white. 
––tint–value, tint_color [bool]
    Set tinting level. Default value: 0 (tinting disabled). 

Also, i have a window drawn around the tray, how do i remove it. I'm using compiz fusion, so it might be something to set in the compoz options rather than stalonetray options.

I don't undertand the effect of those options :
––window-layer layer, window_layer layer
    Sets the EWMH–compliant layer of tray`s window. Possible values for layer: bottom, normal, top. Default value: normal. 
––window-type type, window_type type
    Sets the EWMH–compliant type of tray`s window. Possible values for type: dock, normal, toolbar, utility. Default value: dock.
–w, ––withdrawn, withdrawn [bool]
    Start in withdrawn (dockapp) mode. NEW in 0.7, prior to that was default mode.

Sorry if this seems stupid, but i made some search on google and didn't found anything looking like a small how-to or guide, and some of those manual entries are not easy to understand without some strong knowledge of window managers inner processes.

---

