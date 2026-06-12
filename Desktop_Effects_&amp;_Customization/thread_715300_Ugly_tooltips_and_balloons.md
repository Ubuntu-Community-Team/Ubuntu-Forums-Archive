---
title: "Ugly tooltips and balloons"
date: 2008-03-04
forum: Desktop Effects &amp; Customization
---

### Post by tom66 on 2008-03-04
I have a blue colour scheme in Ubuntu, but my large balloons/tooltips have this ugly brown/yellow colour next to the nice blue...

[IMG]http://i30.tinypic.com/29uoxls.jpg[/IMG]

How can I change this? 

**Edit: ** I'm not sure this belongs here, but this is the closest place I could find.

Thanks!
Tom

---

### Post by PinkFloyd102489 on 2008-03-04
Id like to know also how to fix this. Mine looks like crap.

---

### Post by tedt on 2008-03-05
I am going to assume you are using Gutsy.  There are two ways to change the look of the tooltips that I know of,  the first is

to open up the Appearance then Customize then Colors and change the "Tooltips" to your desired color.


The second is:

you can add this line to your current gtkrc

style "tooltips" = "default"
{
  	bg[NORMAL] = "#D4D4D2"
}
class "GtkTooltips" style "tooltips"
widget "gtk-tooltips" style "tooltips"


this will make the background kind of white.  you can change the bg to other colors.  the bar should match the selected color.  i think you are limited in changing the strip color.

---

