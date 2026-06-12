---
title: "customize Ubuntu panel"
date: 2010-07-18
forum: Desktop Environments
---

### Post by yunintegral on 2010-07-18
hi 
[http://5angh0.shworks.com/images/desktop/1.png](http://5angh0.shworks.com/images/desktop/1.png) in this screenshot, how can i change panel button's background image into just black color?

i apply "Glossy P" theme and i modify ~/.gtkrc-2.0 like this:
> 
style "my_panel"
{
bg_pixmap[NORMAL] = ".themes/panel/gray-neu.png"
fg[NORMAL] = "#ffffff"
bg[NORMAL] = "#000000"
fg[ACTIVE] = "#000000"
bg[ACTIVE] = "#dfdfdf"
fg[SELECTED] = "#000000"
bg[SELECTED] = "#efefef"
fg[PRELIGHT] = "#000000"
bg[PRELIGHT] = "#ffffff"
}

widget "*PanelWidget*" style "my_panel"
widget "*PanelApplet*" style "my_panel"
widget "*fast-user-switch*" style "my_panel"
class "PanelApp*" style "my_panel"
class "PanelToplevel*" style "my_panel"
widget_class "*Mail*" style "my_panel"
widget_class "*notif*" style "my_panel"
widget_class "*Notif*" style "my_panel"


i think i can solve this problem by assign image file in option like this --> "bg[PRELIGHT] = "image.png""
but it is occur error
how can i do this?

---

