---
title: "[xubuntu] Remove icons from Window Buttons in Taskbar?"
date: 2014-08-14
forum: Desktop Environments
---

### Post by tylergreenwich on 2014-08-14
Is there a way to only display the label of active applications in the window buttons section of the taskbar, instead of both the label and icon? I found a check mark within the Window Buttons settings of the panel to either activate or deactivate the button label, but not the icon itself.

---

### Post by Toz on 2014-08-14
Hello and welcome to the forums.

To remove the icon from the Window Buttons display, you need to override a setting. To do so, create the file **$HOME/.gtkrc-2.0** with the following content:
```

### Remove icon display from the Window Buttons plugin
style "xfce-tasklist-style"
{
  XfceTasklist::minimized-icon-lucency = 0
}
class "XfceTasklist" style "xfce-tasklist-style"
```
...and restart the panel:
```
xfce4-panel -r
```

---

### Post by tylergreenwich on 2014-08-14
Worked perfectly! Thanks so much.

---

### Post by tylergreenwich on 2014-08-14
Is there also a way to unbold (or unborder) the currently used app?

---

### Post by Toz on 2014-08-14
> **tylergreenwich said:**
> Is there also a way to unbold (or unborder) the currently used app?

Yup. Add this code to the bottom (below the previous snippet) of the .gtkrc-2.0 file:
```

##############################################################################
#panel transparency tweak
style "mypanel" 
{
      engine "pixmap"
        {
                image
                {
                        function                = BOX
                        recolorable             = TRUE
                        state                   = PRELIGHT
                        file                    = "panel-button-hover.png"
                        border                  = { 1, 1, 0, 0 }
                        stretch                 = TRUE
                }
                image
                {
                        function                = BOX
                        recolorable             = TRUE
                        state                   = ACTIVE
                        file                    = "panel-button-hover.png"
                        border                  = { 1, 1, 0, 0 }
                        stretch                 = TRUE
                }
        }
}

widget "*tasklist*"                style "mypanel"
```

You'll also need to download and save [this image]("http://img99.imageshack.us/img99/6641/panelbuttonhover.png") in your home directory and name it **panel-button-hover.png**.

---

### Post by tylergreenwich on 2014-08-14
You're amazing!

---

### Post by wangmerc on 2015-04-20
> **Toz said:**
> Yup. Add this code to the bottom (below the previous snippet) of the .gtkrc-2.0 file:

Thanks you for both tweaks, they are works perfect. I have two more questions similar like you disscused above. Here it is:

**1.) **How to make the same tweak for menu and notify buttons? They are have borders too when mouse over it, see the pic below:
[IMG]http://cs623922.vk.me/v623922304/25fdd/TdRo91vmfag.jpg[/IMG][IMG]http://cs623922.vk.me/v623922304/25fe4/aQdXwC25Ocw.jpg[/IMG]

**2.)** Second issue is also connected with buttons, please check the picture below. 
[IMG]http://cs623922.vk.me/v623922304/25feb/nPt9FZUL-qM.jpg[/IMG]

You can see here five applications launched in the one time, four of them are rolled up and one active is chrome browser. Somehow icon of the current active application are shifted down for the few pixels from original state, you can see it on the picture. And the question is - How to turn off this feature? I want to leave all buttons straight in one line, no matter launched they are or not. (Same effect if you just move mouse cursor over the icon without clicking on it)

I'm using xubuntu 14.04 LTS with xfce 4.10. I would be very grateful for the help. Thanks you.

---

### Post by Toz on 2015-04-20
1. Add the following snippet after **widget "*whiskermenu*"              style "mypanel"**:
```

widget "*whiskermenu*"              style "mypanel"
widget "*applicationsmenu*"        style "mypanel"

```
...the first one is for the whisker menu, the second for the applications menu.

I've never been able to remove the highlighting from the xfce4-indicator-plugin (what your are referring to as "notify buttons"). It is a GTK3 plugin so perhaps the answer lies in GTK3 theme directives. I haven't looked.

2. I notice this as well. Unfortunately, there is no property override that fixes this. If you want to follow this through, perhaps you could create a bug report for it.

---

### Post by wangmerc on 2015-04-20
> **Toz said:**
> 1. Add the following snippet after **widget "*whiskermenu*"              style "mypanel"**:
```

widget "*whiskermenu*"              style "mypanel"
widget "*applicationsmenu*"        style "mypanel"

```
...the first one is for the whisker menu, the second for the applications menu.

I've never been able to remove the highlighting from the xfce4-indicator-plugin (what your are referring to as "notify buttons"). It is a GTK3 plugin so perhaps the answer lies in GTK3 theme directives. I haven't looked.

2. I notice this as well. Unfortunately, there is no property override that fixes this. If you want to follow this through, perhaps you could create a bug report for it.

1. My mistake, you are right, that isn't xfce4-indicator-plugin, i prefer use other plugins for each indicator (tbt i can't remember the reason why), anyways, i done with it, just added the same snippets with all indicators i need. 

2. It's not a big deal, just a little annoying thing.

Thank you very much for help, Toz!

---

### Post by Toz on 2015-04-20
For #2, try this:
```
style "button-press" {
        GtkButton               ::child-displacement-x                  = 0
        GtkButton               ::child-displacement-y                  = -1
}
widget "*tasklist*" style "button-press"
```
...it seems to have an effect. Adjust the values as required.

---

### Post by wangmerc on 2015-04-20
(-1) Y axis move it up for a few pixels,  but if leave (0) it's save original position, no more movement.

Works perfect! Bless you!

---

