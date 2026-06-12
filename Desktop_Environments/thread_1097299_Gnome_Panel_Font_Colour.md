---
title: "Gnome Panel Font Colour"
date: 2009-03-15
forum: Desktop Environments
---

### Post by s.fox on 2009-03-15
Hi,

I have been looking into a way to change the font colour on my gnome panel to white.  I have been able to successfully follow [this]("http://ubuntuforums.org/showpost.php?p=1988074&postcount=1") guide. :D

As mentioned above it did manage to turn ALL the font on my gnome panel to white,  but how would I only have the top level items in white and child items in black?  Is it even possible?

Unfortunately it has also turned the font for all of my menu items for other applications  to white.  For example in terminal File, Edit, View are now in an unreadable white colour :(  Does anybody know how I get around/ fix this problem?

Many thanks 

-Ash R

---

### Post by inobe on 2009-03-15
next to window background should be darker than text

---

### Post by s.fox on 2009-03-16
> **inobe said:**
> next to window background should be darker than text

Sorry,I don't understand what you mean. 

Could you maybe post an example of how it should look in the gtkrc-2.0 file?   

Many thanks,

Ash R

---

### Post by mcduck on 2009-03-16
Actually quite simple, the code in the post you linked simply applies the color to many other places than just panel applets. Simply removing those lines makes it only change color of panel applets:

```
style "my_color"
{
fg[NORMAL] = "#ffffff"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
```

---

### Post by 73ckn797 on 2009-03-16
> **Ash R said:**
> Hi,

I have been looking into a way to change the font colour on my gnome panel to white.  I have been able to successfully follow [this]("http://ubuntuforums.org/showpost.php?p=1988074&postcount=1") guide. :D

As mentioned above it did manage to turn ALL the font on my gnome panel to white,  but how would I only have the top level items in white and child items in black?  Is it even possible?

Unfortunately it has also turned the font for all of my menu items for other applications  to white.  For example in terminal File, Edit, View are now in an unreadable white colour :(  Does anybody know how I get around/ fix this problem?

Many thanks 

-Ash R

Go into Synaptic and download "gnome-color-chooser". That will be what you are looking for.

---

### Post by s.fox on 2009-03-16
> **73ckn797 said:**
> Go into Synaptic and download "gnome-color-chooser". That will be what you are looking for.

Hi,

That program looks pretty swish.  Can't seem to spot where I would set the font colour though, or for that matter the background colour to the desktop switcher :(  

Thanks for the application though

EDIT:  After some more tinkering I have got it sorted out.   

Thank you very much,  much appreciated

---

### Post by 73ckn797 on 2009-03-16
You are welcome.

---

