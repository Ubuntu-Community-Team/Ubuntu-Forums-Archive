---
title: "Desktop icons text not seen after install Dorian-Dark Theme"
date: 2015-01-10
forum: Desktop Environments
---

### Post by gubtan on 2015-01-10
Hi all,

I installed Dorian-Dark Theme on Xubuntu 14.04. After the installation the text of the desktop icons were in a "bubble" (label), but I didn't like it. I browsed in the net that how can I change the text of the desktop icons and I found this:

```

    style "xfdesktop-icon-view" {
      ## opacity of text background (0 - 255, 0 = transparent)
      XfdesktopIconView::label-alpha = 0
      XfdesktopIconView::selected-label-alpha = 100

      ## text background colors
      base[NORMAL]    = "#EDECEB"
      base[ACTIVE]    = shade (0.8, "#86ABD9")
      base[SELECTED]  = "#86ABD9"

      ## text foreground colors
      fg[NORMAL]      = shade (0.9, "#FFFFFF")
      fg[ACTIVE]      = shade (0.8, "#FFFFFF")
      fg[SELECTED]    = "#FFFFFF"

      ## whether or not unselected icon text gets truncated (...)
      # XfdesktopIconVIew::ellipsize-icon-labels = 1

      ## text shadow to be painted with the icon labels
      XfdesktopIconView::shadow-x-offset = 2
      XfdesktopIconView::shadow-y-offset = 2
      XfdesktopIconView::shadow-color = "#000000"
      XfdesktopIconView::selected-shadow-x-offset = 2
      XfdesktopIconView::selected-shadow-y-offset = 2
      XfdesktopIconView::selected-shadow-color = "#000000"

      ## spacing and sizing of icons on the grid
      # XfdesktopIconVIew::cell-spacing = 6
      # XfdesktopIconView::cell-padding = 6
      # XfdesktopIconView::cell-text-width-proportion = 2.5
    }
    widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```

I made a file with this name ".gtkrc-2.0" and I pasted the code then save it in the HOME directory. I logged out and Logged in but the text of the desktop icons not seen. If I click on any desktop icon 1 time the text is visible. I changed the color in the code, but not working.

Please help me, how can I change the text of the desktop icons color? My background is black, it would be good the text will be white without "bubble" (label).

I look forward to solutions.

Regards,

gubtan

---

### Post by Dennis N on 2015-01-10
> how can I change the text of the desktop icons color? My background is black, it would be good the text will be white without "bubble" (label).

Setting **label-alpha = 0** makes the background behind the text transparent; **label-alpha  =  100** is no transparency. Your code makes it normally transparent but with a solid background color when you click on it.

**fg[NORMAL] = "#FFFFFF"** will set the text to white when it's not selected. You can change **shade (0.9, "#FFFFFF")** to [B]"#FFFFFF"
[/B]
**fg[SELECTED] = "#FFFFFF"** will set the text to white when selected. It is already set to white for selected text. 

use **gcolor2** to find color codes for other colors.

Be sure you downloaded the 3.10 version of the theme, and not one of the others - they may not work correctly.

---

### Post by gubtan on 2015-01-11
Dennis N,

Thank you for your reply, but not working. The text of the desktop icons not seen.

Regards,

gubtan

---

### Post by Dennis N on 2015-01-11
Hey gubtan,

I downloaded the theme to check it out. Here's how I got it working. I am using Xubuntu 14.04. I put my theme folder in ~/.themes Then I opened the file gtkrc (which is inside the theme's gtk-2.0 folder) in my text editor. I added the following lines at the very bottom and saved:

```
style "xfdesktop-icon-view" {
#   Uncomment the line below for transparent icon backgrounds.
     XfdesktopIconView::label-alpha = 0
     XfdesktopIconView::selected-label-alpha = 90
     XfdesktopIconView::shadow-x-offset = 0
     XfdesktopIconView::shadow-y-offset = 0
     XfdesktopIconView::selected-shadow-x-offset = 1
     XfdesktopIconView::selected-shadow-y-offset = 1
     XfdesktopIconView::shadow-color = "#333333"
     XfdesktopIconView::selected-shadow-color = "#333333"

     base[NORMAL] = "#30334A"
     base[ACTIVE] = "#8F8F8F"
     base[SELECTED] = "#636363"

     fg[NORMAL] ="#FFFFFF"
     fg[ACTIVE] = "#FFFFFF"
     fg[SELECTED] = "#FFFF00"

}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"


```I have white text with the desktop icons. The text becomes yellow when selected. 

Delete the file you added to your home folder, as it will override this gtkrc. After finalizing any settings, you can copy the theme folder into /usr/share/themes.

---

### Post by gubtan on 2015-01-11
> **Dennis N said:**
> Hey gubtan,

I downloaded the theme to check it out. Here's how I got it working. I am using Xubuntu 14.04. I put my theme folder in ~/.themes Then I opened the file gtkrc (which is inside the theme's gtk-2.0 folder) in my text editor. I added the following lines at the very bottom and saved:

```
style "xfdesktop-icon-view" {
#   Uncomment the line below for transparent icon backgrounds.
     XfdesktopIconView::label-alpha = 0
     XfdesktopIconView::selected-label-alpha = 90
     XfdesktopIconView::shadow-x-offset = 0
     XfdesktopIconView::shadow-y-offset = 0
     XfdesktopIconView::selected-shadow-x-offset = 1
     XfdesktopIconView::selected-shadow-y-offset = 1
     XfdesktopIconView::shadow-color = "#333333"
     XfdesktopIconView::selected-shadow-color = "#333333"

     base[NORMAL] = "#30334A"
     base[ACTIVE] = "#8F8F8F"
     base[SELECTED] = "#636363"

     fg[NORMAL] ="#FFFFFF"
     fg[ACTIVE] = "#FFFFFF"
     fg[SELECTED] = "#FFFF00"

}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"


```I have white text with the desktop icons. The text becomes yellow when selected. 

Delete the file you added to your home folder, as it will override this gtkrc. After finalizing any settings, you can copy the theme folder into /usr/share/themes.

YIppiiiiii! It works!

Thank You!

---

### Post by Dennis N on 2015-01-11
Hey Gubtan, Thanks for the feedback and glad to learn that it is all working ok!

---

