---
title: "Need more info customising panel colour using .gtkrc"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Fafnir on 2006-06-04
OK, so I decided to take off the default theme and move to something more customised (I know, I'm a wicked, wicked heathen :-D). Which went fine, but then I wanted to change the panel colours, since they now clashed. After googling, I found out that in order to change any characteristics of the panels other than basic background colour (like colour for a selected entry), and thereby avoid perpetrating a hideous crime against nature, I need to create a file called .gtkrc-2.0 in my home directory in the following format:

```

style "panel"
{
   fg[NORMAL]               = "#FFFFFF"
   fg[PRELIGHT]            = "#FFFFFF"
   fg[ACTIVE]               = "#FFFFFF"
   fg[SELECTED]            = "#FFFFFF"
#  fg[INSENSITIVE]            = "#8A857C"

   bg[NORMAL]               = "#5472C7"
   bg[PRELIGHT]            = "#183CA0"
   bg[ACTIVE]               = "#183CA0"
   bg[SELECTED]            = "#5472C7"
#  bg[INSENSITIVE]            = "#EFEFEF"

#  base[NORMAL]            = "#ffffff"
   base[PRELIGHT]            = "#0000DD"
#  base[ACTIVE]            = "#D0D0D0"
   base[SELECTED]            = "#0000DD"
#  base[INSENSITIVE]         = "#E8E8E8"

#  text[NORMAL]            = "#161616"
#  text[PRELIGHT]            = "#000000"
#  text[ACTIVE]               = "#000000"
#  text[SELECTED]            = "#ffffff"
#  text[INSENSITIVE]            = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"
```

Unforunately, there doesn't seem to be much documentation out there! I think I've worked out what the RGB values do for the following entries:

```
fg[NORMAL]     // Normal text colour
bg[NORMAL]     // Background in the static locations the Panel Properties menu
               // doesn't touch, like around the Show Desktop button
fg[PRELIGHT]   // Text colour of an unselected program with the cursor over it
bg[PRELIGHT]   // Background colour of an unselected program with the cursor over it
base[PRELIGHT] // Border colour of a selected menu item
fg[ACTIVE]     // Text colour of a selected program
bg[ACTIVE]     // Background colour of a selected program
fg[SELECTED]   // Text colour of a selected menu item
base[SELECTED] // Background colour of a selected menu item
```

I'm completely clueless on the rest, though - I've tried setting them to outlandish values (e.g. bright magenta) to test for them, and failed to find them. Also, I can't seem to find the value for the background/text colour of a *selected* program with the cursor over it. The other thing I've been having trouble with is adding transparency to the values - it's possible from the Panel Properties menu, but as I said, that only works for the background colour.

Any chance of some more information? I'm afraid I don't really know enough about GTK for finding out myself to be an option...

Thanks in advance!

---

### Post by adam.tropics on 2006-06-06
As far as I know, you can't add transparency in that way, for individual components whilst working at that level. I am told you would have to rewrite the gtk engine. Not quite so simple! 

I customized mine with guidance from gnomedev.com, and it suits me, but it was frankly trial and error...

```
style "panel"
{
  fg[NORMAL]               = "#ffffff"
  fg[PRELIGHT]            = "#000000"
  fg[ACTIVE]               = "#ffffff"
  fg[SELECTED]            = "#000000"
  fg[INSENSITIVE]            = "#8A857C"
  bg[NORMAL]               = "#4D4D4C"
  bg[PRELIGHT]            = "#4D4D4C"
  bg[ACTIVE]               = "#4D4D4C"
  bg[SELECTED]            = "#4D4D4C"
  bg[INSENSITIVE]            = "#4D4D4C"
 base[NORMAL]            = "#4D4D4C"
  base[PRELIGHT]            = "#4D4D4C"
  base[ACTIVE]            = "#4D4D4C"
  base[SELECTED]            = "#4D4D4C"
  base[INSENSITIVE]         = "#4D4D4C"

  text[NORMAL]            = "#ffffff"
  text[PRELIGHT]            = "#ffffff"
  text[ACTIVE]               = "#ffffff"
  text[SELECTED]            = "#ffffff"
  text[INSENSITIVE]            = "#ffffff"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
```

Sorry I can't be more help!

---

### Post by Fafnir on 2006-06-08
Thanks for the sample file!

I've just updated to Dapper, and it seems that one of the upgrades was altering the scope of the Panel Properties transparency setting - now it covers just about everything on the panel, a massive improvement! It's not manual control, and I still need the .gtkrc file to control colour, but the combination now does everything I'm after.

So, to anyone in my place: upgrade to Dapper!

PS - Sorry for the late reply! Real life intruded in the form of A Levels, a couple of teething troubles with Dapper, and most importantly a season 1 Firefly box set... :-)

---

### Post by adam.tropics on 2006-06-08
lol, been away from uk for 5 years (moved here from Cheltenham.....better weather! ), had to google firefly!!

Yep the transparency handling has changed, though as I underastand it, it is less that the transparency has changed than now the panel components actually pay attention! Good news for gaim, network manager etc etc, basically the notification area. It is still pseudo transparency, but it turns out this is a good thing, as for example I am using xgl and compiz and so have real transparency available. All good, except if used on the panel (example) the whole panel fades away, text and all!!

---

