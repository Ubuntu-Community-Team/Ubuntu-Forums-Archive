---
title: "I need Ubuntu Human color scheme colors."
date: 2008-03-26
forum: Desktop Effects &amp; Customization
---

### Post by michaelfougnie on 2008-03-26
I want to make Amarok fit in better, and need the hex code of the color of the objects in ubuntu.

---

### Post by Blacklife08 on 2008-03-26
Well, im sure there is a better way to do this somehow, but if u take a screenshot of a part of the human interface that u want
then import that image into a photo editor, use the eyedropper tool to find what the color is, and then from there with it as the current color u should be able to somewhere change modes so it shows the hex.

Just an idea in theory.  
hope it works

---

### Post by Cherry Cotton on 2008-04-04
This should help! It's from /usr/share/themes/Human/gtk-2.0/gtkrc on my system (running Ubuntu "Hardy Heron"), and cleaned up by me::

```
fg_color:                 #101010
bg_color:                 #EFEBE7
base_color:               #FFF
text_color:               #000
selected_bg_color:        #FFD799
selected_fg_color:        #000
tooltip_bg_color:         #F5F5B5
tooltip_fg_color:         #000
orange_color:             #FF6D0C
metacity_frame_color:     #CC863E
extra_view_widgets_color: #F5C07F
```

---

